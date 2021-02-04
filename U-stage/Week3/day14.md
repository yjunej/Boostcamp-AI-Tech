
# Day 14 - RNN

## RNN MHA

```

class MultiHeadedAttention(nn.Module):
    def __init__(self,d_feat=128,n_head=5,actv=F.relu,USE_BIAS=True,dropout_p=0.1,device=None):
        """
        :param d_feat: feature dimension
        :param n_head: number of heads
        :param actv: activation after each linear layer
        :param USE_BIAS: whether to use bias
        :param dropout_p: dropout rate
        :device: which device to use (e.g., cuda:0)
        """
        super(MultiHeadedAttention,self).__init__()
        if (d_feat%n_head) != 0:
            raise ValueError("d_feat(%d) should be divisible by b_head(%d)"%(d_feat,n_head)) 
        self.d_feat = d_feat
        self.n_head = n_head
        self.d_head = self.d_feat // self.n_head
        self.actv = actv
        self.USE_BIAS = USE_BIAS
        self.dropout_p = dropout_p # prob. of zeroed

        self.lin_Q = nn.Linear(self.d_feat,self.d_feat,self.USE_BIAS)
        self.lin_K = nn.Linear(self.d_feat,self.d_feat,self.USE_BIAS)
        self.lin_V = nn.Linear(self.d_feat,self.d_feat,self.USE_BIAS)
        self.lin_O = nn.Linear(self.d_feat,self.d_feat,self.USE_BIAS)

        self.dropout = nn.Dropout(p=self.dropout_p)
    
    def forward(self,Q,K,V,mask=None):
        """
        :param Q: [n_batch, n_Q, d_feat]
        :param K: [n_batch, n_K, d_feat]
        :param V: [n_batch, n_V, d_feat] <= n_K and n_V must be the same 
        :param mask: 
        """
        n_batch = Q.shape[0]
        Q_feat = self.lin_Q(Q) 
        K_feat = self.lin_K(K) 
        V_feat = self.lin_V(V)
        # Q_feat: [n_batch, n_Q, d_feat]
        # K_feat: [n_batch, n_K, d_feat]
        # V_feat: [n_batch, n_V, d_feat]

        # Multi-head split of Q, K, and V (d_feat = n_head*d_head)
        Q_split = Q_feat.view(n_batch, -1, self.n_head, self.d_head).permute(0, 2, 1, 3)
        K_split = K_feat.view(n_batch, -1, self.n_head, self.d_head).permute(0, 2, 1, 3)
        V_split = V_feat.view(n_batch, -1, self.n_head, self.d_head).permute(0, 2, 1, 3)
        # Q_split: [n_batch, n_head, n_Q, d_head]
        # K_split: [n_batch, n_head, n_K, d_head]
        # V_split: [n_batch, n_head, n_V, d_head]

        # Multi-Headed Attention
        d_K = K.size()[-1] # key dimension
        scores = Q_split.matmul(K_split.permute(0,1,3,2))/np.sqrt(d_K)
        if mask is not None:
            scores = scores.masked_fill(mask==0,-1e9)
        attention = torch.softmax(scores,dim=-1)
        x_raw = torch.matmul(self.dropout(attention),V_split) # dropout is NOT mentioned in the paper
        # attention: [n_batch, n_head, n_Q, n_K]
        # x_raw: [n_batch, n_head, n_Q, d_head]

        # Reshape x
        x_rsh1 = x_raw.permute(0,2,1,3).contiguous()
        # x_rsh1: [n_batch, n_Q, n_head, d_head]
        x_rsh2 = x_rsh1.view(n_batch,-1,self.d_feat)
        # x_rsh2: [n_batch, n_Q, d_feat]

        # Linear
        x = self.lin_O(x_rsh2)
        # x: [n_batch, n_Q, d_feat]
        out = {'Q_feat':Q_feat,'K_feat':K_feat,'V_feat':V_feat,
               'Q_split':Q_split,'K_split':K_split,'V_split':V_split,
               'scores':scores,'attention':attention,
               'x_raw':x_raw,'x_rsh1':x_rsh1,'x_rsh2':x_rsh2,'x':x}
        return out
```

- RNN, transformer의 mha를 pytorch로 작성하였습니다.
- nn.Module을 상속받아 class를 만듭니다.
- super를 사용하여 부모 class의 init의 attribute를 사용합니다.
- 여러개의 head로 나누어 어텐션 계산이 이루어집니다.
- 각 input과 output의 차원을 출력합니다.


# 피어세션
## To Do List
- 수업중 모르겠던거나 유용하다고 생각하는것 공유
- 다른 캠퍼들이 올린 질문 보기 - 답변이 올라오지 않은 질문의 경우 다음날 토의 결정
- futher question: pytorch model 불러오기
- 나만의 데이터셋 주제 정하기 - 자유

## Question
- 학습 기록 잘하는법!

## 내일까지 할 것
- 오늘의 과제 완수하기












 
 
  


  

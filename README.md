# NJCS-
2019真题答案
若对部分答案有歧义欢迎讨论
1.D
2.A
3.A
4.D
5.B
6.C
7.C
一般可以理解为复杂度小的可以归约到大的，从而任意一个NP问题都可以规约到NPC问题。
8.C
9.C
10.
11.A
12.B
13.D
加减法操作数不区分无符号还是有符号，而乘法必定区分。
14.C
-129.5D = - 1000 0001 .1B 转化为s+e^(127+p)+f;s=1,p=7,f=0000 0011;结果1 1000 0110 0000 0011 000...0B;16进制C30180000H
15.C
16.D
17.A
21.
  1)队空rear==front;队满(rear+1)%m==front;这种方法会牺牲一个存储空间;
  2)(rear+m-front)%m
  3)进队出队返回值若为true则成功，否则失败;
    class que{
      private:
              type a[m];
              int rear,front;
      public:
              bool enQueue(type x);
              bool deQueue(type &x);
    }
    bool enQueue(type x){
      if((rear+1)%m==front) return false;
      a[++rear] = x;
      return true;
    }
    bool deQueue(type &x){
      if(rear == front) return false;
      x = a[front--];
      return true;
    }
22.
  1)         
     34-------> 16,34 ----------->   19      ------------->   19        ------------>  19      ------------>    19,34
                                    /  \                    /    \                    /   \                    /   |   \
                                16       34               16      21,34             5,16   21,34            5,16   21   49
  2)设返回一个三元组
    sturct tri{
      BtreeNode *ptr;
      bool suc;
      int index;
    }
    tri Search(int x,BtreeNode *root){
        BtreeNode *p = root,*q = NULL;
        tri res;
        while(p!=NULL){
            int i=0;
            while(i<p.n&&p->key[i]<x) i++;
            if(p->key[i]==x){
                res.ptr = p;
                res.suc = true;
                res.index = i;
                return res;
            }
            q = p;
            p = p->ptr[i];
        }
        res.ptr = q;
        res.index = -1;
        res.suc = false;
        return res;
    }
23.
   1)二叉树遍历时间都是O(n),递归深度为O(n)
     int height(Tnode* t){
         if(t==NULL) return -1;
         return 1+max(height(t->leftchild),height(t->rightchild));
     }
   2)直径即左子树的深度+1加上右子树的深度+1 +1
     int dist(Tnode *t){
         if(t==NULL) return 0;
         return height(t->leftchild)+height(t->rightchild)+3;
     }
24.
   1) int *solution(int x){
          int i=0;
          int res[n];
          while(x){
             res[i++] = x/2^(n-i-1);
             x %= 2^(n-i-1);
          }
          return res;
      }  
   这是一个贪心算法，因为由二进制可知任何一个2^n之内的数可唯一表示。因为2^n-1=1+2+2^2+...+2^(n-1);2^n=2*2^(n-1)所以不存在一个数可以用更少的面值的数表示，因此为贪心。
   2) 设面值数组value[n]={d1,d2,...,dn};dp数组res[N]表示兑换N元最少的钱数;
      res[0] = 0;
      for(int i=i;i<N+1;i++){
          int mincount = MAX_INT;
          for(int j=0;j<n&&value[j]<=i;j++)
              mincount = min(res[i-value[j]]+1,mincount);
          res[i] = mincount;
      }
      算法时间复杂度为O(n^2);空间复杂度为O(n);
25.
   semaphore pa1=pa2=pa3=pb1=pc1=pd1=0;
   cobegin
      p1(){
          V(pa1);
          V(pa2);
          V(pa3);
      }
      p2(){
          P(pa1);
          P(pc1);
          V(pb1);
      }
      p3(){
          P(pa2);
          V(pc1);
      }
      p4(){
          P(pa3);
          V(pd1);
      }
      p5(){
          P(pb1);
          p(pd1);
      }
   coend
26.
   1) 2KB/4B = 2^9
   2) 页内偏移log2(2KB) = 11位;一级页表log2(2KB/4B) = 9位;二级页表32 - 11 - 9 = 12;
   3) 2GB/2KB = 2^20
   4) 合理 2M/2k*4B = 4KB,页表项大小共4KB远小于内存
   5)             2  1  4  2  3  1  3  1  5
          编号5   2  2  2  2  2  2  2  2  5
          编号10     1  1  1  3  3  3  3  3
          编号20        4  4  4  1  1  1  1
                  √  √  √     √  √        √
          缺页次数6；缺页率2/3
          4104/2048=2...8;对应块号为20则物理地址20*2048+8 = 40968
27.
   1)





2018真题答案







# Basic recipe for deep learning

The following flowchart in suggested by [[Andrew Ng]] in the [[Coursera specialization on deep learning]].

```mermaid

graph TD

S[start]
A{"high bias?<br>(training set performance)"} 
C{"high variance?<br>(dev set performance)"}
B["bigger network<br>train longer<br>(other NN architecture?)"]
D["more data<br>regularization<br>(other NN architecure?)"]
E[done]
S --> A
A --N--> C
A --Y--> B
B --> S
C --N--> E
C --Y--> D
D --> S
```

Thus, as long as we can make the network bigger and add more data, there is not [[bias-variance tradeoff]].
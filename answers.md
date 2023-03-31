# CMPS 2200 Recitation 6
## Answers

**Name:**___Jiayi Xu______________________


Place all written answers from `recitation-06.md` here for easier grading.



- **d.**

File | Fixed-Length Coding | Huffman Coding | Huffman vs. Fixed-Length
|------|---------------------|----------------------|------------------|
f1.txt    |    1340              |     826           |0.6164
alice29.txt    |  1039367                |     676374           |0.6508
asyoulik.txt    |  876253                   |   606448             |0.6921
grammar.lsp    |     26047                |     17356           |0.6663
fields.c    |       78050              |     56206           |0.7201

We can see that the ratio of Huffman coding cost to fixed-length coding cost is consistently less than 1 for all the files, indicating that Huffman coding is more efficient than fixed-length coding.


- **e.**

For every document which every character had the same frequency, let $f$ be frequency and $t$ be total number of characters:

 If number of distinct characters is equal to $2^n$ for integer n, every character will have the same length of bits, and the cost will be `numOfBits*t*f`, where `numOfBits` is $\log_2 (t)$.
 
 If number of distinct characters is not equal to $2^n$ for integer n, all character will be at last two level on a huffman tree, that is, all have $\lfloor \log_2 (t) \rfloor$(notation for floor) or $\lceil \log_2 (t) \rceil$(ceiling) bits.For example, for t=5, some characters have 2 bits and others have 3 like this {'C': '00', 'D': '01', 'E': '10', 'A': '110', 'B': '111'}. Then, the cost will be as follow: 
 
 $f*t*\lfloor \log_2 (t) \rfloor$ < cost < $f*t*\lceil \log_2 (t) \rceil$

 More specifically, cost is 
 
 $f*(t-2^{(\lfloor \log_2 (t) \rfloor)})*2*\lceil \log_2 (t) \rceil+f*(2^{(\lfloor \log_2 (t) \rfloor)}*2-t)*\lfloor \log_2 (t) \rfloor$ 
 
 where the middle parts $(t-2^{(\lfloor \log_2 (t) \rfloor)})*2$ and $(2^{(\lfloor \log_2 (t) \rfloor)}*2-t)$ are number of characters corresponding to $\lceil \log_2 (t) \rceil$ and $\lfloor \log_2 (t) \rfloor$ bits. 
 
 Take {'C': '00', 'D': '01', 'E': '10', 'A': '110', 'B': '111'} as an example, number of 3 bits characters is `(5-4)*2=2` and 2 bits is `4*2-5=3`

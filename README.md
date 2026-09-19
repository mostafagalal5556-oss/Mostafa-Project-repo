# Network Request Tracing & Response Analysis



## Tracing Diagram

```mermaid

flowchart TD

    Hop1[Browser / Terminal - Local PC] -->|1. DNS Lookup| Hop2[Local / ISP Router]

    Hop2 -->|2. Forward Request| Hop3[ISP DNS / Network Node]

    Hop3 -->|3. TCP + TLS Handshake| Hop4[Google Edge Network / CDN Node]

    Hop4 -->|4. Reverse Proxy / Gateway| Hop5[Google Web Server 'gws']

    Hop5 -->|5. HTTP Response 200 OK| Hop1 


يعنى ببساطة الامور بتمشرى بالمحطات التالية 
1- الجهاز الشخصى بتاعى بيجهز الطلب وبيدور فى ال dns cache عن الip الخاص بجوجل 
2- راوتر البيت واللى بينقل الطلب الى الانترنت خارجيا 
3-isp network & dns
ودا مقدم الخدمة فى وى واللى بيترجم جوجل الى ip
4- بيدور على اقرب سيرفر لشبكة جوجل بالقرب من المنطقة اللى انا عايش فيها لتقليل وقت الاستجابة والاحمال 
5- تمر الامور الى ان تعود الاستجابة بشكل عكسى للمحطات السابقة بكود http 200 ok
فيه كود html وملفات كوكيز لغاية ما توصلى على الجهاز والشاشة بتاعتى 
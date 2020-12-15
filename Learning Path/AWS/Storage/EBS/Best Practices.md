# Best Practices

Recall that Amazon EBS volumes are network-attached and not directly attached to
the host like instance stores. On instances without support for Amazon EBS–optimized
throughput, network traffic can contend with traffic between your instance and your
Amazon EBS volumes. On Amazon EBS–optimized instances, the two types of traffic
are kept separate. Some instance configurations incur an extra cost for using Amazon
EBS–optimized, while others are always Amazon EBS–optimized at no extra cost.
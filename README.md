# toxic-combination
toxic-combination

Problem Definition: If the search count N on the combination of filter on customer attributes (K1,K2,...Kp), N < the threshold e.g. 5, then that combination (K1,K2,..Kp) is toxic, because we can easily identify the customer based on the customer attributes K1,K2,...Kp.


Example Case:
Customer 1 has account balance 500k, and live in Wan Chai.  The Search filter combination is: low income and living district.
Filter 1 of low income K1 is defined as account balance < 100, and balance >=100, so in case of customer 1, filter function K1(500k) = ">= 100".
Filter 2 of living district is defined as (Island,Kowloon, NT), so in case of customer 1, filter function K2("Wan Chai") = "Island".
If we have ~1 million customer data, and count them based on the 2 attribute filters, we will get the search count matrix, e.g.
          balance<100 , balance>=100
Island      4         ,     30k
Kowloon     1000      ,     30k
NT          10k       ,     30k

Since there are only 4 customers having balance<100, and living in hk island, so "balance<100" and "Living in Island" is a toxic combination.

The search count matrix can be computed by the following MapReduce phase:
Map Phase:
    eimit( [

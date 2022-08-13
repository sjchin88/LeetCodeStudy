# Transform and Conquer

Problems:



1567\. Maximum Length of Subarray With Positive Product

[https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/](https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/)

{% embed url="https://leetcode.com/problems/maximum-length-of-subarray-with-positive-product/" %}

Keys:

The product of the numbers is positive if the total number of negative numbers included is even. We can use two figures to keep track of the current length of the number which resulted in a positive product (positiveLength), and the current length of the number which resulted in a negative product (negativeLength).&#x20;

To update the figures:

1. If the current number is 0; reset the two figures
2.  If current number > 0; increase positiveLength by 1.&#x20;

    if the negativeLength is not zero (ie, some of the previous numbers contain negative numbers), increase the negativeLength by 1 as well.&#x20;
3. If current number < 0; the negativeLength become positiveLength + 1; If the original negativeLength == 0; the positiveLength become 0; else positiveLength = negativeLength+1;

Compare the positiveLength with maxLength recorded and update the maxLength accordingly.&#x20;

We only need one iteration of the list of number. Time complexity = O(n). Space complexity = O(1)&#x20;





&#x20;

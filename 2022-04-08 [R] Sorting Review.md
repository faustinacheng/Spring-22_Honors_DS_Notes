8 Apr 2022

<img src="images/image-20220427024105595.png" alt="image-20220427024105595" style="zoom:50%;" />

Runtime: O(n^2^)



<img src="images/image-20220427024311283.png" alt="image-20220427024311283" style="zoom:50%;" />

Runtime: Best Case: O(n), Worst Case: O(n^2^)



<img src="images/image-20220427024655674.png" alt="image-20220427024655674" style="zoom:50%;" />

- Method to pick pivot can drastically change runtime, especially in average case

<img src="images/image-20220427024830274.png" alt="image-20220427024830274" style="zoom:33%;" />

Usually can break down until 2 or 3 elements then sort them using whatever sorting method you prefer.



<img src="images/image-20220427025049078.png" alt="image-20220427025049078" style="zoom:50%;" />

- Bucket sort is a pretty bad choice for this array because there are only 6 elements in the array but the range of the values is much larger: 1 - 45
- Need to know what the possible values are for bucket sort
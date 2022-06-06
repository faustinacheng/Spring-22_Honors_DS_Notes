## Floyd-Warshall Algorithm

- NOT ON FINAL

Initialize with Adjacency Matrix:

<img src="images/image-20220507165059938.png" alt="image-20220507165059938" style="zoom:33%;" />

<img src="images/image-20220507165258686.png" alt="image-20220507165258686" style="zoom: 25%;" />

<img src="images/image-20220507165408594.png" alt="image-20220507165408594" style="zoom:25%;" />

Implementation:

<img src="images/image-20220507165529759.png" alt="image-20220507165529759" style="zoom:39%;" />

<img src="images/image-20220507165725180.png" alt="image-20220507165725180" style="zoom:35%;" />

Iterate through all vertices k:

<img src="images/image-20220507165800946.png" alt="image-20220507165800946" style="zoom:33%;" />

<img src="images/image-20220507165814407.png" alt="image-20220507165814407" style="zoom:33%;" />

For each vertix k, loop through all vertices u and all vertices v

- First obtain cost to go from u - v via k

<img src="images/image-20220507170046144.png" alt="image-20220507170046144" style="zoom:33%;" />

<img src="images/image-20220507170155573.png" alt="image-20220507170155573" style="zoom:33%;" />

<img src="images/image-20220507170306992.png" alt="image-20220507170306992" style="zoom:33%;" />

<img src="images/image-20220507170322447.png" alt="image-20220507170322447" style="zoom:33%;" />

<img src="images/image-20220507170417820.png" alt="image-20220507170417820" style="zoom:35%;" />

<img src="images/image-20220507170455896.png" alt="image-20220507170455896" style="zoom:33%;" />

<img src="images/image-20220507170546826.png" alt="image-20220507170546826" style="zoom:33%;" />

<img src="images/image-20220507170625146.png" alt="image-20220507170625146" style="zoom:33%;" />

<img src="images/image-20220507170716824.png" alt="image-20220507170716824" style="zoom:33%;" />

<img src="images/image-20220507170800298.png" alt="image-20220507170800298" style="zoom:33%;" />

<img src="images/image-20220507170812900.png" alt="image-20220507170812900" style="zoom:33%;" />

<img src="images/image-20220507170904019.png" alt="image-20220507170904019" style="zoom:33%;" />

<img src="images/image-20220507171024264.png" alt="image-20220507171024264" style="zoom:33%;" />

<img src="images/image-20220507171558558.png" alt="image-20220507171558558" style="zoom:33%;" />

<img src="images/image-20220507171924486.png" alt="image-20220507171924486" style="zoom:33%;" />

<img src="images/image-20220507172042398.png" alt="image-20220507172042398" style="zoom:33%;" />

<img src="images/image-20220507172138423.png" alt="image-20220507172138423" style="zoom:33%;" />

- Result

<img src="images/image-20220507172523873.png" alt="image-20220507172523873" style="zoom: 25%;" />




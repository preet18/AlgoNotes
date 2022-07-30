[Maximum Expression](https://www.algoexpert.io/questions/maximize-expression)

https://www.techiedelight.com/maximize-value-of-the-expression/

### Approach 1 - Brute Force (Using Nested forloop)
import java.util.*;
``` Java
class Program {
  // Complexity O(N^4)
  public int maximizeExpression(int[] array) {
    if(array.length<4) return 0;
    int max = Integer.MIN_VALUE;
    int n = array.length;
    for(int i=0; i<n; i++){
      for(int j=i+1; j<n; j++){
        for(int k=j+1; k<n; k++){
          for(int l=k+1; l<n; l++){
            int sum = array[i]-array[j]+array[k]-array[l];
            max = Math.max(sum, max);
          }
        }
      }
    }
    return max;
  }
}
```

### Apprroach 2 - Dynamic Programming

``` Java

class Program {
// O(4*N) Time and Space.
  public int maximizeExpression(int[] array) {
    if(array.length<4) return 0;
    int n = array.length;
    int[][] mat = new int[4][n];

    mat[0][0] = array[0];
    mat[1][0] = mat[2][0] = mat[2][1] = mat[3][0] = mat[3][1] = mat[3][2] = Integer.MIN_VALUE;

    for(int i=1; i<array.length; i++){
      mat[0][i] = Math.max(mat[0][i-1], array[i]);
    }

    for(int i=1; i<array.length; i++){
      mat[1][i] = Math.max(mat[1][i-1], mat[0][i-1] - array[i]);
    }

    for(int i=2; i<array.length; i++){
      mat[2][i] = Math.max(mat[2][i-1], mat[1][i-1] + array[i]);
    }

    for(int i=3; i<array.length; i++){
      mat[3][i] = Math.max(mat[3][i-1], mat[2][i-1] - array[i]);
    }

    return mat[3][n-1];
  }
}
```

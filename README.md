# Python_DSA

## Taking suffix matrix of a 2D array
```python

def suffix_product_matrix(mat):
    n = len(mat)
    m = len(mat[0])

    # Initialize suffix matrix with 1s
    suffix = [[1] * m for _ in range(n)]

    for i in reversed(range(n)):
        for j in reversed(range(m)):
            suffix[i][j] = mat[i][j]

            if j + 1 < m:
                suffix[i][j] *= suffix[i][j + 1]

            if i + 1 < n:
                suffix[i][j] *= suffix[i + 1][j]

            if i + 1 < n and j + 1 < m:
                suffix[i][j] //= suffix[i + 1][j + 1]  # remove double count

    return suffix
```

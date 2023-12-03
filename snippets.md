# Useful stuff

---
---

## ▫️ bash

### Zipping

* General unzip: `unzip path/to/your/file.zip`
* Unzip to specific path: `unzip path/to/your/file.zip -d path/to/destination/folder`

---

## ▫️ **git**

### ghh CLI

* Create new repo: `gh repo create ___ --private`

### Commands

* Remove local already-pushed file from remote:

  ```git
  git rm --cached FILE_OR_DIR_NAME
  git commit -m "Removed FILE_OR_DIR_NAME from repository"
  git push origin master
  ```

<!-- *  -->
---

## ▫️ numpy

* RESHAPING
  * The reshape() function takes a single tuple argument that specifies the new shape of the array
    * Used frequently to _add_ a dimension of when for libs like sklearn and keras (to the END of the shape tuple -- i.e. **right-padding with 1s**)
  * In the case of reshaping 1-D `(m,)` --> 2-D `(m,1)`:
    * Tuple would be the shape of the array as the first dimension (data.shape[0]) and 1 for the second dimension:
      * `data.shape == (m_old, )` (e.g. `(1000,)`)
      * `data = data.reshape( (m_old, n_new)  )`
      * `data.shape == (m_old, n_new)` (e.g. `(1000, 1)`)
* BROADCASTING
In formal LinAlg, arithmetic can only be performed when:  

* the shape of each dimension in the arrays are equal (even for dotproduct - though not matmul)
  
However, in ML, we often want to add **A** `(m,n)` to **v** `(,n)`.  
NumPy enables this by _broadcasting_ the vector to the shape of the matrix.  
Specifically np (**which considers vectors as (n,) since it is row-oriented**) effectively:

1. **Left-pads with 1s** the dimensions of the smaller array
2. **Right-to-left compares** the dimensions of the two arrays and ensures either:
   a. The dimensions are equal **OR**
   b. At least one of the dimensions is 1
3. If all dimensions pass, the smaller array is replicated (_broadcast_) along the dim(s) where it is 1 to match the shape of the larger array.

**NOTE**: Broadcasting is not a copy operation. It is a view of the original array with the same data. This means that if you modify a broadcasted array, it modifies the original array.  

So for example:  

* 1-D vs. 2-D
  * LOOKS like comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (3,)  
  * ACTUALLY np is comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,3)  
* 2-D vs. scalar  
  * LOOKS like comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,)  
  * ACTUALLY np is comparing:  
    * A.shape -- (2,3)  
    * b.shape -- (1,1)

---

<!-- ##  -->
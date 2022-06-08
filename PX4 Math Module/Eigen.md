# Eigen Library

### Notes:
- Naming convention:
``` C++ 
//<Vector/Matrix/RowVector><# of col, "X" for undefined/needs specifying><data type>
Eigen::Matrix3d a; //3x3 double matrix
Eigen::VectorXf; //float vector of size x by 1

```
- Dynamic Allocation
```C++
Eigen::Matrix<float, Dynamic, Dynamic> //dynamic for both row and column
Eigen::Matrix<float, Dynamic, 2> //dynamic for row, with 2 columns

```

### Appendix I: CMake Integration with PX4
- [[CMake]]
### Appendix II: References
- [Eigen Official Documentation](https://eigen.tuxfamily.org/dox/index.html)
- [Quick Reference Page](https://eigen.tuxfamily.org/dox/group__QuickRefPage.html)



#math 
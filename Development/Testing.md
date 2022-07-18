# Testing

## 1. Types of Testing

PX4 uses Google Test ('GTest'), and offers three types of testing:
- Unit tests (w/ GTest)
- Functional tests (w/ GTest)
- SITL test

### A. Unit Tests
- Assertions -> Tests -> Test Suites -> Test Fixture -> Test Program
```c++
ASSERT_EQ(1,2) << "Fatal Error" // fatal, aborts current function
EXPECT_EQ(1,2) << "Non Fatal"// non-fatal, continues
```
- ```ASSERT``` vs ```EXPECT```
	- Error message can be slipped in the above form
	- clean-up is needed for ```ASSERT_```

### B. Function Tests

## 2. Integrating Testing into [[ROS]]
### A. Procedure:
- Link test in package `CMakeLists.txt`
- run `colcon build` then run test executable in src folder

## Appendix: References
- [Official PX4 Doc](https://docs.px4.io/v1.12/en/test_and_ci/unit_tests.html)
- [GTest](https://google.github.io/googletest/primer.html)


#development 
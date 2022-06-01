# Quaternion for Rotation

### Euler's Rotation Theorem
- In 3-d space, any displacement of a rigid body such that there exist a fixed point is equivalent to a rotation around an axis that runs through the fixed point
- Axis-angle representation: a unit vector $\hat{e}$, and a rotation angle $\theta$ . 

### Quaternion Setup
- quaternion has the following form
$$q = q_0 + q_1 i + q_2 j + q_3 k$$
where $i$, $j$, and $k$ can be interpreted as either unit vectors or imaginary operators

- If we interpret $i$, $j$, and $k$ as unit vectors, then quaternions have the following form

$$q = \begin{bmatrix} q_0 \\ q^r \end{bmatrix}$$where $q_r$ is the vector part of the quaternion

### Quaternion Multiplication
- If we express quaternion in imaginary operator form, then multiplication follows associative law:

$$p * q = (p_0 + p_1 i + p_2 j + p_3 k) * (q_0 + q_1 i + q_2 j + q_3 k)$$
note:
$$i^2 = j^2 = k^2 = -1,\; ij = k = -ji,\; ki = j = -k,\; jk = i = -kk$$
- If we express quaternion in vector form, then

$$p*q = \begin{bmatrix}p_0q_o - (p^r\cdot q^r) \\ p_0 q^r + q_0p^r + p^r \times q^r\end{bmatrix}$$

### Quaternion Properties
- Noncommutativity
- Norm $$norm(q) = \sum_{i=0}^{i=3} q^2_i$$
- Inverse: $$q^{-1} = \frac{1}{norm(q)} \cdot (q_0, -q^r)$$
- Norm of product
$$norm(p*q) = norm(p)\cdot norm(q)$$
- Asscociativity over multiplication
- Quaternion Inverse:
$$q*q^{-1} = \begin{bmatrix} \sum q_i^2\end{bmatrix}$$
if $q$ is unit quaternion, then the product between $q$ and its inverse is the identity quaternion

- Inverse of product
$$(p*q)^{-1} = q^{-1}*p^{-1}$$

### Unit Quaternion as Rotation
Very similar to [[#Euler's Rotation Theorem]], quaternion visualizes a fixed amount of rotation around an **unit vector** in the form of $i, j$ and $k$. 

$$q = e^{\frac{\theta}{2}(e_x i + e_y j + e_z k)} = \cos{\frac{\theta}{2}} + (e_x i + e_y j + e_z k)\sin{\frac{\theta}{2}}$$

 Left-hand rotation of vector $\vec{u}$ around $\vec{n}$ thru an angle $\theta$
$$q = \begin{bmatrix}\cos(\theta/2) \\ \sin(\theta/2)n^r\end{bmatrix}$$
$$u = q^{-1} * u * q$$

- **Quaternion has a double cover**
- Quaternion can be converted into DCM form
	- [Ref](!https://www.mathworks.com/help/aerotbx/ug/quatrotate.html)

#math 
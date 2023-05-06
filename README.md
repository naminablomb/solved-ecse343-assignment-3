Download Link: https://assignmentchef.com/product/solved-ecse343-assignment-3
<br>
Note: You can write the function in the appendix section using the provided stencils.

<strong>Question 1: </strong>

<ol>

 <li>For two given matrices no !</li>

</ol>

if A= [0 0, 1 0] and B = [0 0, 0 1]

e^A = I + A + (A^2)/2! + (A^3)/3! + (A^4)/4! + … = [1 0, 1 1] e^B = I + B + (B^2)/2! + (B^3)/3! + (B^4)/4! + … = [1 0, 0 e]

e^A e^B =  (I + A + (A^2)/2! + (A^3)/3! + (A^4)/4! + …)(I + B + (B^2)/2! + (B^3)/3! + (B^4)/4! + …) = [0 0, 1 1]

(A+B)^2 = [0 0, 1 1] = (A+B)

e^(A+B) = [1 0, e-1 e] not equal to e^A e^B

<ol>

 <li>Under what condition is ? Elaborate. e^A e^B = e^(A+B) if and only if A and B are commute, AB = BA.</li>

</ol>

<strong>Question 2:  Eigenvalues!</strong>

<ol>

 <li>a) The Power Iteration method is used to compute the dominant eigen value and the eigen vector associated with the  dominant eigen value of a given matrix. Any random vector  can be written as the linear combination of n independent eigen vectors of a matrix  as</li>

</ol>




On multiplying the above with matrix A we get,




The vectors                                                                                                    . The symbol  denotes the




Equation (3), can be  generalised to




Without loss of generality (4) can be written as




Assuming that                                  .  As            , the terms with  .  Thus, as

converges to the eigen vector           corresponding to the largest eigen value. Write an iterative algorithm which computes the eigen vector and eigen value using the following recurssive formula,




where

, where        is the input tolerance value.

<u>Write a MATLAB function power_method</u>(<u>A</u>,<u>tol</u>)<u> that uses power iteration al</u>g<u>orithm to compute the dominant ei</u>g<u>en value and the ei</u>g<u>envector. </u>

<u>Note: The stencil for this function is provided in the Appendix and </u>y<u>ou should complete it there.</u>

Use the cell below to test the your fucntion, you can use MATLAB’s built in function, eig (see MATLAB documentation) to compare your answers.

<ol>

 <li>b) The eigen vectors of the <strong>real and symmeteric </strong>matrices are orthogonal to each other. We can use this fact along with the power iteration method to compute all the eigen values and eigen vectors. The idea is to compute the first dominant eigne vector and then project out the previous eigen vectors using the Gram-Schmidt approch. Given that we computed the first      eigen vectors, , we can use the power iteration algorithm to compute the , as following,</li>

</ol>

<em>Step 1. Start with a arbitrary intial guess vector </em>

<em>Step 2. Project out the previous eigen vectors using the Gram-Schmidt,</em>

<em>        </em>

<em>Step 3. Carry out the power iteration using the recurssive formula, </em>

<em>Step 4. Check for convergence, if </em><em> repeat steps 2 and 3.</em>

The above method is prone to numerical errors, therefore, the above algorithm is seldomly used.  Instead we use a more stable verison of this algorithm which performs the orthogonalisation process described in Step 2, sumultaneously on all the vectors.

In the <strong>simulatanous orthogonalisation </strong>method we start with  matrix containing the initial guesses for all eigen vectors,

The most obivious choice for the intial guess matrix is an identity matrix of same size as matrix  In the next step we carry out the power iteration on the Intial guess matrix.

Since we know that eigen vectors of symmeteric and real matrices are othogonal to each other, so we orthogonalise and normalise the columns of the matrix . The most obvious choice is to perform QR decompostion on matrix  as shown below,




The use of QR decompostion is the obivious choice because the columns of    are orthonormal. Next we carry out the power iteration by multiplying the columns of the matrix           with     This process can be summerised as,

<em>Step 1. Start with initial guess for all eigen vectors using matrix, </em><em>.</em>

<em>Step 2. Compute the power iteration </em><em>.</em>

<em>Step 3. Get </em><em>, the matrix containing orthogonalised and normalised the columnn of  </em><em>. Use QR decomposition to obtain </em><em>.</em>

<em>Step 4. Check for convergence, if </em><em>, repeat steps 2 and 3.</em>

<u>Write a MATLAB function <em>simultaneous_ortho</em></u><em>g<u>onalisation</u>(<u>A</u>,<u>1e-4) </u></em><u>to compute the all ei</u>g<u>en values and ei</u>g<u>en vectors usin</u>g<u>  <strong>simulataneous-ortho</strong></u><strong>g<u>onalisation </u></strong>,<u> the function should take the matrix and tolerance as inputs</u>. <u> Use the same matrix as part (a). </u>

<u>Please do NOT write the Gram-Schmidt based ortho</u>g<u>onalisation method.</u>

Use the cell below to test the your function.

[V1,eigen1] = simultaneous_orthogonalisation(A,1e-4)

V1 = 5×5

-0.3539    0.2217    0.2944   -0.6493   -0.5633

-0.5184   -0.2130   -0.3790    0.5038   -0.5370

-0.3418    0.0704   -0.7231   -0.4533    0.3871

-0.4869   -0.6734    0.4140   -0.0898    0.3606    -0.5021    0.6686    0.2747    0.3331    0.3382 eigen1 = 5×1

16.1870     2.6447     1.3806     0.5387

0.0190

<ol>

 <li>c) The QR-algorithm is the standard algorithm for computing the eigen values. As you can surely guess, this involves the QR-factorization of the matrix in question. This algorithm proceeds by computing the QR transfrom of the given matrix A as</li>

</ol>

Next, the we right multiply the above equation with

Next we compute the QR decomposion of




Again, the we right multiply the above equation with

We can repeat the above procedure for k iterations, and we get the following

It can be shown  and diagonal of the matrix converges to eigen values.

<u> Write a MATLAB function,<em> QR_al</em></u><em>g<u>orithm</u>(<u>A</u>,<u>1e-4)</u></em>,<u> that implements the QR-al</u>g<u>orithm to compute all the ei</u>g<u>en values of the matrix <strong><em>A</em></strong>. Use the same matrix as part(a).</u>

V2 = 5×5

-0.3539    0.2217    0.2944   -0.6493   -0.5633

-0.5184   -0.2130   -0.3790    0.5038   -0.5370

-0.3418    0.0704   -0.7231   -0.4533    0.3871

-0.4869   -0.6734    0.4139   -0.0898    0.3606    -0.5021    0.6686    0.2747    0.3331    0.3382 eigen2 = 5×1

16.1870     2.6447     1.3806     0.5387     0.0190

Question 3):  Consider the following data found in the file DataPCA.mat:

The data has already been normalized so that it can be approximated by a line passing through the origin. We aim to find the best linear approximation for this data in the form:

Your task is to find the paramter a and plot the linear approximation. We will use two methods. First, we will use the Linear Regression based approach to find the best straight line fit. Secondly, we will use first principal component to obtain the best linear approximation as follows:

Principal Component Analysis aims to find the direction of maximum variation in the data. It can be shown that the direction of maximum variation (the best linear approximation) aims to reduce to the orthogal distance between in the data points and the best linear aproximation.  This can be seen in Figure 1 below,

Figure 1.Figure shows the orthogonal distance, , between the line v and data point

We are given n data points the columns of the matrix <strong>X</strong> contains the data points ranging from 1 to n. We need to find the direction of vector,  v, which reduces the orthogonal distance,      , for n data points.  Since we are only interested in the direction of vector, we can safely assume             . This formulated mathematically as,




The above equation can be formulated to form a equaivalent maximization problem shown below, <em>(for detailed derivation consult Chapter 6 of  Numerical Algorithms by Justin Solomon)</em>

It can be shown that the eigen vector corresponding to the dominant eigen value, maximises the above equation. The vector v is known as the principal component of the dataset. It can be computed using the Power Iteration method.

Use your power iteration method written in Question 2 part (a) to compute the dominant eigen vector. You can also use the MATLAB’s function eig()  to coompute the eigen vector.

Use the above two approaches and plot the best straight line fit through the data on the same graph. Comment on the results, explain any differences/similarities in both approaches. What is the error being minimized in each case?

0.2804     1.0000

a = v(2)/v(1)

a = 3.5657

y_pca = a*x_plot

y_pca = 1×100   -10.6971  -10.4810  -10.2649  -10.0488   -9.8327   -9.6166   -9.4005   -9.18

Appendix Write the code for the function here.

You can use the space below to write any additional funcitons if needed.
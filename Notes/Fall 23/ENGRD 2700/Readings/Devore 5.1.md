### Two Discrete Random Variables
- Let X and Y be two discrete random variables defined on the sample space S of an experiment. The joint PMF p(x,y) is defined for each pair of numbers (x,y) by $$p(x,y)=P(X=x, Y=y)$$
- $$P[(X,Y)\in A]=\sum\sum_{(x,y\in A)}p(x,y)$$
- The marginal PMF of X $$p_x(x)=\sum_yp(x,y)$$ for each possible value of x
### Two Continuous Random Variables
- Let X and Y be continuous random variables. A joint PDF $f(x,y)$ for these two variables is a function satisfying $f(x,y)\geq0$ and $$\int_{-\infty}^\infty\int_{-\infty}^\infty f(x,y)dxdy=1$$
- For any two dimensional set A $$P[(X,Y)\in A]\iint_Af(x,y)dxdy$$
- The marginal PDF function of X and Y $f_x(x)$ and $f_y(y)$ $$f_x(x)=\int_{-\infty}^\infty f(x,y)dy$$ $$f_y(y)=\int_{-\infty}^\infty f(x,y)dx$$
### Independent Random Variables
- Two random variables X and Y are independent if for every pair of x and y values $$p(x,y)=p_x(x)p_y(y)$$ for the discrete case 
- $$f(x,y)=f_x(x)f_y(y)$$ for the continuous case
### More than Two Random Variables
- If $X_1,\cdots,X_n$ are all discrete random variables their joint PMF is $$p(x_1,\cdots,x_n)=P(X_1=x_1,\cdots,X_n=x_n)$$
- If the variables are continuous the joint PDF of $X_1,\cdots,X_n$ is the function $f(X_1,\cdots,X_n)$ such that for any n intervals $$P(a_1\leq X_1\leq b_1,\cdots,a_n\leq X_1\leq b_n)=\int_a^b\int_a^bf(x_1,\cdots,x_n)dx_ndx_1$$
- The random variables are independent if for every subset of the variables the joint PMF or PDF of the subset is equal to the products of the marginal PMF or PDF
### Conditional Probability
- Let X and Y be two continuous random variables with joint PDF f(x,y) and marginal X PDF $f_x(x)$. Then for any X value x for which $f_x(x)>0$ the conditional PDF of Y given X=x $$f_{y|x}(y|x)=\frac{f(x,y)}{f_x(x)}$$
- If X and Y are discrete replace PDF with PMF
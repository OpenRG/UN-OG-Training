(Chap_Numpy)=
# NumPy

<div>
  <iframe id="inlineFrameExample"
      title="Inline Frame Example"
      width="100%"
      height="700"
      src="https://acme.byu.edu/00000181-448a-d778-a18f-dfcae22f0001/intro-to-python">
  </iframe>
</div>


# Exercises


```{exercise-start}
:label: ExerNumpy-array
```
Create a Numpy array `b` (defined this as the savings of 2 agents (the rows) over 5 periods (the columns)):
   $$ \[
b=
  \begin{bmatrix}
    1.1 & 2.2 & 3.0 & 2.0 & 1.0 \\
    3.3 & 4.4 & 5.0 & 3.7 & 2.0
  \end{bmatrix}
\].
$$
  Use the `shape` method of NumPy arrays to print the shape of this matrix.  Use array slicing to print the first row of `b`, which represents the lifecycle savings decisions of the first agent (i.e., the amount they choose to save in each of their 5 periods of life).  Use array slicing to print the second column of `b`, which is the saves of both agents when they are in their second period of life.  Finally, use array slicing to print the first two rows and the last three columns of `b` (i.e., the savings of both agents from middle age onwards).
```{exercise-end}
```

```{exercise-start}
:label: ExerNumpy-dotproduct
```
Now let's think about the matrix `b` are representing not two individual agents, but two types of agents who live for five periods.  In this way, we will interpret the values in `b` as the total savings of different cohorts of these two types of agents who are all living together at a point in time.  Now, define a matrix `\Omega`:
     $$ \[
\Omega=
  \begin{bmatrix}
    0.05 & 0.05 & 0.08 & 0.06 & 0.2 \\
    0.12 & 0.16 & 0.03 & 0.2 & 0.05
  \end{bmatrix}
\].
$$
`Omega` represents the fraction of agents in the economy of each type/cohort (Note that the elements of `Omega` sum to 1). Use matrix multiplication to find `B`, which is the dot product of `b` and the transpose of `Omega`. What does `B` represent?
```{exercise-end}
```

```{exercise-start}
:label: ExerNumpy-mult
```
Multiply the matrix `b` by the matrix `Omega` element-wise (Hadamard product).  Use the `np.array.sum()` method on the resulting matrix to find the total savings of each cohort.
```{exercise-end}
```

```{exercise-start}
:label: ExerNumpy-zeros
```
In one line, create a matrix of zeros that is the same size as `b`.
```{exercise-end}
```

```{exercise-start}
:label: ExerNumpy-where
```
Use `np.where` to return the elements of `b` that are greater than 2.0 and zero elsewhere.
```{exercise-end}
```

```{exercise-start}
:label: ExerNumpy-stack
```
Now suppose a 3rd type of agent.  This agent has savings $b_3 = \[4.1, 5.1, 7.1, 4.5, 0.9]$.  Use `np.vstack` to stack `b` on top of `b_3` to create a new matrix `b_new`.
```{exercise-end}
```
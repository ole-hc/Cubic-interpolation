# Cubic-interpolation-
This repository provides a small algorithm to turn a set of n points into n - 1 cubic splines. As well as an algorithm to calculate systems of equations. Currently only natural cubic splines are supported. z

# Usage
You can either define a vector of points to which cubic interpolation is automatically applied, or you can define matrices in the Ax = B style that then can then be solved for x.

## Cubic-Interpolation
Definition of the point vector:
```
vector<Point> dataPoints = {
  {1.0f, 2.0f},
  {3.0f, 3.0f},
  {5.0f, 9.0f},
  {8.0f, 10.0f}
};
```
then further calculations can be made:
```
Graph dataGraph = Graph(dataPoints); // you need to create a graph object to use more in depth calculations 
vector<Matrix> soe;
soe = dataGraph.createMatrixes();    // this returns the system of equations given a natural cubic interpolation
SystemOfEquations interpolation = SystemOfEquations(soe.at(0), soe.at(1)); // SystemOfEquations (SoE) allows for further calculations regarding SoE
interpolation.printSystemOfEquations(); // This prints the full Ax = B style SoE to the terminal
```

If you only want to calculate a specific SoE then you can use the following setup:
```
// first define matrix A und C
// Here we defined Ax = B as  a * b = c
vector<vector<float>> aValues = {
  {4.0f, 5.0f, 2.0f},
  {3.0f, 4.0f, 1.0f},
  {3.0f, 6.0f, 3.0f}
};
Matrix a = Matrix(3, 3, aValues);

vector<vector<float>> cValues = {
  {-1.0f},
  {-1.0f},
  {8.0f}
};
Matrix c = Matrix(1, 3, cValues);

// Here the real calculation is done
SystemOfEquations interpolation = SystemOfEquations(a, c);
interpolation.printSystemOfEquations();
```

There are also a few more commands for matrices etc. like matrix.printMatrix(), ...

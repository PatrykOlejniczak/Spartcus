# Spartcus

Spartacus program to generate datasets according to given constraints. 
Output sets in the form of spreadsheets can be used with machine learning algorithms (mostly mathematican programming models). The project is written using .Net Core and .Net Standard.

[![Build Status](https://dev.azure.com/patrykolejniczak/Spartacus/_apis/build/status/PatrykOlejniczak.Spartacus?branchName=master)](https://dev.azure.com/patrykolejniczak/Spartacus/_build/latest?definitionId=1?branchName=master) [![NuGet Version and Downloads count](https://buildstats.info/nuget/Spartacus.Generator)](https://www.nuget.org/packages/Spartacus.Generator) 

## Sample output
The sets are in the form of a list of points in the N-dimensional space (X1-XN) together with a column representing the result (Y) that defines whether the point meets the restrictions.

| X1 | X2 | X3 | Y  |
|:--:|:--:|:--:|:--:|
| 10 | 15 | 12 | 0 |
| 0  | 8  | 6  | 1 |
| 2  | -8 | 12 | 0 |

Table: Sample output xlsx datasheet without extensions

<br />

| X1 | X2 | X3 | X1+X2 | X1+X3 | X2+X3 | Y  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 10 | 15 | 12 | 25 | 22 | 27 | 0 |
| 0  | 8  | 6  | 8  | 6  | 14 | 1 |
| 2  | -8 | 12 | -6 | 14 | 4  | 0 |

Table: Sample output xlsx datasheet with enable linear extension (--linear true)

<br />

| X1 | X2 | X3 | X1\*X1 | X1\*X2 | X1\*X3 | X2\*X2 | X2\*X3 | X3\*X3 | Y  |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 10 | 15 | 12 | 100 | 150 | 120 | 225 | 180 | 144 | 0 |
| 0  | 8  | 6  | 0 | 0  | 0  | 64 | 48 | 36 | 1 |
| 2  | -8 | 12 | 4 |-16 | 24 | 64 | 96  | 144 | 0 |

Table: Sample output xlsx datasheet with enable quadratic extension (--quadratic true)

## Available predefined benchmarks:
+ Cube
+ Ball
+ Simplex

### Rules for generating points

![Visualization](/docs/images/formulated_benchmarks.JPG)

Image: Benchmark formulated as MP models

### Available parameters

| Paramater | Description | Sample used | Required |
|:---------:|:-----------:|:-----------:|:--------:|
| --points  | Number of points to generate | --points 5000 | Yes |
| --outputpath  | Path to storage generated data | --outputpath C:\Desktop | No (def: UserDirectory) |
| --output  | File name (without extension) | --output cube2n | Yes |
| --sheets  | List of sheets in generated file | --sheets dataset1 dataset2 | No |
| --linear  | Generate additional columns with linear dependencies | --l true | No |
| --quadratic  | Generate additional columns with quadratic dependencies | --q false | No |
| --seed  | Seed for MersenneTwister | --seed 123 | No |

Table: Common parameters for all benchamarks

<br />
<br />

| Paramater | Description | Sample used | Required |
|:---------:|:-----------:|:-----------:|:--------:|
|--constant|Parameter used to bound variables (d in formulas)|--constant 5| No (def: 2.7) |
|--dimensions|Number of dimensions|--diemnsions 2|No (def: 2) |

Table: Parameters only for Cube and Simplex

<br />
<br />

| Paramater | Description | Sample used | Required |
|:---------:|:-----------:|:-----------:|:--------:|
|--radius|Radius of ball|--radius 5| No (def: 2.7) |
|--center|Center of ball (affects the number of dimensions -> X1, X2, X3 etc) |--center 1 2 3 |Yes|

Table: Parameters only for Ball

<br />

## How to use
Run [build.cmd](scripts/build.cmd). 

### Samples

![](/docs/images/sample_definition.JPG)

|![](/docs/images/cube_sample_1_symbol.JPG)|![](/docs/images/cube_sample_2_symbol.JPG)|![](/docs/images/cube_sample_3_symbol.JPG)|
|:---------:|:-----------:|:-----------:|
|![](/docs/images/cube_sample_1.JPG)|![](/docs/images/cube_sample_2.JPG)|![](/docs/images/cube_sample_3.JPG)|

<br />

|![](/docs/images/simplex_sample_1_symbol.JPG)|![](/docs/images/simplex_sample_2_symbol.JPG)|![](/docs/images/simplex_sample_3_symbol.JPG)|
|:---------:|:-----------:|:-----------:|
|![](/docs/images/simplex_sample_1.JPG)|![](/docs/images/simplex_sample_2.JPG)|![](/docs/images/simplex_sample_3.JPG)|

<br />

|![](/docs/images/ball_sample_1_symbol.JPG)|![](/docs/images/ball_sample_2_symbol.JPG)|![](/docs/images/ball_sample_3_symbol.JPG)|
|:---------:|:-----------:|:-----------:|
|![](/docs/images/ball_sample_1.JPG)|![](/docs/images/ball_sample_2.JPG)|![](/docs/images/ball_sample_3.JPG)|

## Contribution
Feel free to make pull request and add something or just create issue with question / suggestion for improvement / report bug.
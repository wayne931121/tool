# tool
uh...just some function I need to use now...do a record....maybe I will use in future?

```py
def cross_product(p1,p2):
    a,b,c = p1
    d,e,f = p2
    return [ b*f-e*c , -1*(a*f-d*c) , a*e-d*b ]

def average(l1):
    return sum(l1)/len(l1)

def sample_variance(l1):
    u = average(l1)
    return sum([((i-u)**2) for i in l1])/(len(l1)-1)

def population_variance(l1):
    u = average(l1)
    return sum([((i-u)**2) for i in l1])/len(l1)

def sample_standard_deviation(l1):
    return sample_variance(l1)**0.5

def population_standard_deviation(l1):
    return population_variance(l1)**0.5

def standard_score(l1):
    u = average(l1)
    o = population_standard_deviation(l1)
    return [(i-u)/o for i in l1]

def unit_vector_2d(v):
    a,b = v
    d = (a**2+b**2)**(1/2)
    return [ a/d , b/d ]

def unit_vector_3d(v):
    a,b,c = v
    d = (a**2+b**2+c**2)**(1/2)
    return [ a/d , b/d , c/d ]

def unit_vector(v):
    d = sum([i**2 for i in v])**(1/2)
    return [i/d for i in v]
```

https://github.com/qt/qtbase/blob/dev/src/gui/math3d/qquaternion.cpp#L672C1

https://j3d.org/matrix_faq/matrfaq_latest.html#Q55
```py
r = [
        [1,2,3],
        [4,5,6],
        [7,8,9],
]

def rotation_matrix_to_quaternion(r):
    scalar = 0
    axis = [0,0,0,0]
    T = 1+r[0][0]+r[1][1]+r[2][2]
    if T > 0.00000001:
        S = (T**0.5)*2
        X = (r[2][1] - r[1][2]) / S
        Y = (r[0][2] - r[2][0]) / S
        Z = (r[1][0] - r[0][1]) / S
        W = 0.25 * S
        axis[0] = X
        axis[1] = Y
        axis[2] = Z
        axis[3] = W
    else:
        s_next = { 1, 2, 0 };
        i = 0;
        if r[1][1] > r[0][0]:
            i = 1;
        if r[2][2] > r[1][1]:
            i = 2;
        j = s_next[i];
        k = s_next[j];
        S = ( (r[i][i] - r[j][j] - r[k][k] + 1)**0.5 ) * 2
        axis[i] = 0.25 * S
        axis[3] = ( r[k][j] - r[j][k] ) / S
        axis[j] = (r[j][i] + r[i][j]) / S
        axis[k] = (r[k][i] + r[i][k]) / S
    return axis

print(rotation_matrix_to_quaternion(r))
```

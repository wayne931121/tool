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
    T = 1+r[0][0]+r[1][1]+r[2][2]
    if T > 0.00000001:
        S = (T**0.5)*2
        X = (r[2][1] - r[1][2]) / S
        Y = (r[0][2] - r[2][0]) / S
        Z = (r[1][0] - r[0][1]) / S
        W = 0.25 * S
    if ( r[0][0] > r[1][1] ) and ( r[0][0] > r[2][2] ): # Column 0: 
        S  = ( ( 1.0 + r[0][0] - r[1][1] - r[2][2] )**0.5 ) * 2;
        X = 0.25 * S;
        Y = (r[1][0] + r[0][1] ) / S;
        Z = (r[0][2] + r[2][0] ) / S;
        W = (r[2][1] - r[1][2] ) / S;
    elif ( r[1][1] > r[2][2] ): # Column 1: 
        S  = ( ( 1.0 + r[1][1] - r[0][0] - r[2][2] )**0.5 ) * 2;
        X = (r[1][0] + r[0][1] ) / S;
        Y = 0.25 * S;
        Z = (r[2][1] + r[1][2] ) / S;
        W = (r[0][2] - r[2][0] ) / S;
    else:  # Column 2:
        S  = ( ( 1.0 + r[2][2] - r[0][0] - r[1][1] )**0.5 ) * 2;
        X = (r[0][2] + r[2][0] ) / S;
        Y = (r[2][1] + r[1][2] ) / S;
        Z = 0.25 * S;
        W = (r[1][0] - r[0][1] ) / S;
    
    return [W,X,Y,Z]

print(rotation_matrix_to_quaternion(r))
```
```py
def direction_to_quaternion(direction, up):
    zAxis = unit_vector(direction)
    xAxis = cross_product(up, zAxis)
    xAxis = unit_vector(xAxis)
    yAxis = cross_product(zAxis, xAxis)
    r = [
        [xAxis[0],yAxis[0],zAxis[0]],
        [xAxis[1],yAxis[1],zAxis[1]],
        [xAxis[2],yAxis[2],zAxis[2]]
    ]
    return rotation_matrix_to_quaternion(r)

direction = [1.0, 15.0, 169.0]
up = [0.9943875074386597, -0.10574121028184891, 0.0035013644956052303]
print( direction_to_quaternion(direction, up) )
```
https://math.stackexchange.com/questions/1375754/clarification-of-definition-of-inverse-with-quaternions
```py
def inverte_quaternion(q):
    return [q[0],-q[1],-q[2],-q[3]]
print( inverte_quaternion([0.10143093019723892, -0.7759947776794434, 0.09897363185882568, 0.6146121025085449]) )
```

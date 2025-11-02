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

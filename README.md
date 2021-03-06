# psoa

**An implementation of the Particle Swarm Optimization algorithm**

The algorithm can be summarized as follows:

* a swarm of moving particles are used to find the extreme value of an objective function  
* each particle has its own position and velocity  
	* use the given function to evaluate particles' positions  
	* results can be compared, depending on whether we want to maximize or minimize the objective function  
* In each step, a particle receives three forces, they are used to update the particle's velocity  
	* a friction force that slows down the particle  
	* a random attraction force towards the particle's previous best position  
	* a random attraction force towards the swarm's previous best position  
* the particle's velocity is then used to update the particle's position  
* if boundary conditions are included, we consider them to be reflecting boundaries, i.e. if the particle move beyond the boundary in one direction, we would  
	* place the particle back onto the boundary  
	* and reverse the particle's velocity in that direction  
* keep updating the particles' positions and velocities until  
	* the swarm's best position converges  
	* or until we reach the preset maximum number of steps 


## Installation:  
```
pip install psoa
```  
or

```
conda install -c wangxiangwen psoa
```

## Example Usage:  
```python
>>> import psoa
>>> import numpy as np
>>> s = psoa.swarm()
>>> obj = lambda x: -((x[0] - 10) ** 2 + (x[1] - 25) ** 2)
>>> s.maximize(obj, dim=2)
([10.0, 25.0], -0.0)
>>> obj2 = lambda x: np.sum([xi ** 2 - 10 * np.cos(2 * np.pi * xi)
>>>                          for xi in x]) + 10 * len(x)
>>> s.minimize(obj2, dim=5, max_iteration=1e5,
>>>            boundaries=((-5.12, -5.12, -5.12, -5.12, -5.12),
>>>                        (5.12, 5.12, 5.12, 5.12, 5.12)))
([-2.8743161872992346e-10,
  2.579205368330527e-09,
  -4.79709591601136e-09,
  -1.0974277510973518e-09,
  4.4227337040162274e-10],
 0.0)
```

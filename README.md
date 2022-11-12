# ProcCiGen

Procedural city generation

Implement [this algorithm](https://www.tmwhere.com/city_generation.html) to create city city layouts, which was implemented from [this article](https://nothings.org/gamedev/l_systems.html) that simplifies the [original paper](https://cgl.ethz.ch/Downloads/Publications/Papers/2001/p_Par01.pdf)


r(ti,ri,metadata)
This is a road segment with the following parameters:
ti = time delay when this particular segment of road should be placed
ri = geometry information about the segment
metadata = info about the segment

Q[]
This is a list of segments that are ready to be placed. From this list, pick the one with the lowest ti value and place it next.

S[]
This is a list of already placed segments

localConstraints(r)
This is a function that checks to see if a currently selected segment can fit into the constrainst of its local environment (other streets, rivers, hills, etc...)

globalGoals(r)
This is a function that creates all possible road segments that can be created from the location and metadata of an input segment

Algorithm:

~~~
create the first segment and add it to Q

while Q is not empty:
  from Q, select r with smallest ti
  check selected r against local constraints
  if selected r fits in localConstraints:
    add selected r to S
    foreach r(tj, rj, qj) produced by globalGoals(ri, qi):
      add r(ti + 1 + tj, rj, qj) to Q
~~~


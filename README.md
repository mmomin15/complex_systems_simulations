# complex_systems_simulations

Generage 1D-diagrams including bifurcations

Gray-scott reaction Diffusion

Dynamics of Gray-Scott system are given by two equations:

𝜕𝑢/𝑑𝑡= 𝑟_𝑢 ∆^2 𝑢−𝑢𝑣^2+𝑓(1−𝑢)

𝜕𝑣/𝑑𝑡= 𝑟_𝑣 ∆^2 𝑣+𝑢𝑣^2−(𝑓+𝑘)𝑣

𝑢 and 𝑣 are concentrations of the chemicals and 𝑈 and 𝑉

𝑟_𝑢 and 𝑟_𝑣 are diffusion rates of 𝑈 and 𝑉

𝑓 is the feed rate of 𝑈 and 𝑘 is consumption rate of 𝑉

𝜕𝑢/𝑑𝑡 and 𝜕𝑣/𝑑𝑡 are the time derivatives describing change in concentration of 𝑈 and 𝑉 over time

The equations are partitioned into two parts for simulation:

The diffusion part is calculated based on the 4 nearest neighbors of a cell based on von Neumann neighborhood
Diffusion[𝑢(𝑖, 𝑗, 𝑡+1)]=𝑢(𝑖+1, 𝑗, 𝑡)+𝑢(𝑖, 𝑗+1, 𝑡), +𝑢 (𝑖−1, 𝑗, 𝑡)+𝑢(𝑖, 𝑗−1, 𝑡)−4∗𝑢(𝑖, 𝑗, 𝑡) 

where 𝑖 and 𝑗 are the coordinates of the given molecules

The interaction part −𝑢𝑣^2+𝑓(1−𝑢) and 𝑢𝑣^2+𝑓(1−𝑢) can be represented as follows

Interaction [𝑢(𝑖, 𝑗, 𝑡+1)]=− 𝑢(𝑖, 𝑗, 𝑡)∗𝑣(𝑖, 𝑗, 𝑡)^2+𝑓(1−𝑢(𝑖, 𝑗, 𝑡))
Interaction [𝑣(𝑖, 𝑗, 𝑡+1)]=𝑢(𝑖, 𝑗, 𝑡)∗𝑣(𝑖, 𝑗, 𝑡)^2−(𝑓+𝑘)𝑣(𝑖, 𝑗, 𝑡)

Finally, state of each cell is updated based on combination of the following rules

𝒖(𝒊, 𝒋, 𝒕+𝟏)=𝑢(𝑖, 𝑗, 𝑡)+ 𝑟_𝑢∗"Diffusion" [𝑢(𝑖, 𝑗, 𝑡+1)]+ Interaction [𝑢(𝑖, 𝑗, 𝑡+1)]

𝒗(𝒊, 𝒋, 𝒕+𝟏)=𝑣(𝑖, 𝑗, 𝑡)+ 𝑟_𝑣∗"Diffusion" [𝑣(𝑖, 𝑗, 𝑡+1)]+ Interaction [𝑣(𝑖, 𝑗, 𝑡+1)]


# Iterated amplitude adjusted Fourier surrogates (IAAFT)


```@setup s
using CausalityTools
using DynamicalSystems
using Plots
```

Generating AAFT surrogates is done as follows.

```@example s
# Generate a dynamical system, create an orbit and extract a time series.
s = CausalityTools.Systems.logistic3()
orbit = trajectory(s, 150)

# Extract our time series. We'll use the first component of the orbit.
x₁ = orbit[:, 1]

# Construct a random shuffle surrogate.
s₁ = iaaft(x₁)

# Plot the time series along with its random shuffle surrogate
timesteps = 1:size(orbit, 1)
plot(timesteps, x₁, label = "x2")
plot!(timesteps, s₁, label = "IAAFT surrogate realization of x2")
xlabel!("Timestep"); ylabel!("Value")
savefig("surr_iaaft-plot.svg"); nothing #hide
```

![](surr_iaaft-plot.svg)
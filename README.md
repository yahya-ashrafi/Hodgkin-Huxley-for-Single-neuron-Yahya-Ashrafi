# Hodgkin-Huxley-for-Single-neuron-Yahya-Ashrafi
The Hodgkin Huxley Equations
We have many of the components of the Hodgkin Huxley equations; we only need to take a few more steps to see the whole set of equations, which will then naturally suggest how they may be generalized.
In the absence of external current injection, the only currents present are those that charge or discharge the capacitance of the membrane due to the opening or closing of the voltage-dependent ion channels. Thus, the total membrane current, I_{tot}, is equal to the sum of the capacitative current (I_{cap}) and the sum of the ionic currents, I_{ionic}, or{\displaystyle 
    I_{tot} = I_{cap} + I_{ionic}. \quad\text{(Equation 1)}}
Since the capacitative current is a function of the rate of change of voltage,{\displaystyle 
    I_{cap} = C \frac{dV_{m}}{dt}. \quad\text{(Equation 2)}}
For the Hodgkin and Huxley model, the sum of the ionic currents is the sum of the leak, sodium and potassium ionic currents:{\displaystyle 
    I_{ionic} = I_{L} + I_{\text{K}^+} + I_{\text{Na}^+}. \quad\text{(Equation 3)}}
Combining Equations 1, 2 and 3, and assuming that the total current sums to zero, since none is being added or subtracted by an external electrode, we obtain{\displaystyle 
    C \frac{dV_{m}}{dt} = -I_{L} - I_{\text{K}^+} - I_{\text{Na}^+}. \quad\text{(Equation 4)}}
Recall that each ionic current can be re-written in terms of the product of its conductance and driving force:{\displaystyle 
    I_{ion} = g_{ion}(V_{m} - E_{ion}), \quad\text{(Equation 5)}}where V_{m} is the membrane voltage and E_{\text{ion}} is the Nernst or equilibrium potential for the ionic species.
So, we can re-write Equation 4 as follows, using Equation 5:{\displaystyle 
    C \frac{dV_{m}}{dt} = -g_{L}(V_{m} - E_{L}) - g_{\text{K}^+}(V_{m} - E_{\text{K}^+}) - g_{\text{Na}^+}(V_{m} - E_{\text{Na}^+}), \quad\text{(Equation 6)}}an equation we saw in Action Potentials II when we looked at the electrical equivalent circuit for the membrane.
Based on the analyses that Hodgkin and Huxley did, we can go further, and fill in the properties of the conductances for the leak, the voltage-dependent potassium channels, and the voltage-dependent sodium channels.
First, recall that the leak current was just a linear function of the driving force; this is the same as saying that g_{L} is just a constant. To emphasize that it is a fixed, maximal value, it is often written with a bar over the top, as \bar{g}_{L}.
Second, recall that the potassium current, as analyzed in the unit before last, depended on the simultaneous activation of four gating elements, whose probability of moving into a conducting state was represented by the symbol n. Hodgkin and Huxley found the best fit for the data by assuming that there were four of these gates. Since they were assumed to act independently of one another, the overall probability of a potassium channel opening was the probability that all four of the gates had switched into a conducting state, or n \times n \times n \times n = n^4. Thus, if the maximum possible conductance for the potassium channels was \bar{g}_{\text{K}^+}, the overall conductance for the potassium channels was{\displaystyle 
    g_{\text{K}^+} = \bar{g}_{\text{K}^+} n^4. \quad\text{(Equation 7)}}
Third, recall that the sodium current, as analyzed in the previous unit, is dependent on the simultaneous activation of three gating elements, whose probability of moving into a conducting state was represented by the symbol m, and another gating element, which was initially open at rest, but then closed with a probability h. Thus, by the same reasoning, if the maximum possible conductance for the sodium channels was \bar{g}_{\text{Na}^+}, the overall conductance for the sodium channels was{\displaystyle 
    g_{\text{Na}^+} = \bar{g}_{\text{Na}^+} m^3 h. \quad\text{(Equation 8)}}
With these additional definitions, we can now rewrite Equation 6 as follows:{\displaystyle 
    C \frac{dV_{m}}{dt} = -\bar{g}_{L}(V_{m} - E_{L}) - \bar{g}_{\text{K}^+}n^4(V_{m} - E_{\text{K}^+}) - \bar{g}_{\text{Na}^+}m^3 h(V_{m} - E_{\text{Na}^+}). \quad\text{(Equation 9)}}
We now need to address a question that we only looked at qualitatively in the previous two units: how do the gating variables, m, n and h, change with time and with voltage?
Hodgkin and Huxley made the simplest assumption for how these gating variable would change with time. Let us focus on the n variable to make the argument more concrete. Conceptually, one can think of it this way: if the probability that the gating variable will begin to conduct is n, where n ranges from 0 to 1, then the probability that it will stop conducting is 1 - n. For example, assume that we are at voltage where the gating variable is highly unlikely to move into the conducting configuration. Say that the probability of its moving into the conducting configuration was 0.1. Then the probability of its not moving into the conducting configuration is 1 - 0.1, or 0.9, since at any instant the gating particle is either in its conducting configuration, or it is not.
How would this probability update with time? They assumed that there would be some rate (call it \alpha_{n}) at which a gate that is currently not conducting would become conducting. Thus, in the next time instant, \Delta t, the change in the probability, \Delta n, would be the rate at which the gate that is not conducting becomes conducting, multiplied by the proportion of gates that are not yet conducting, which we said was 1 - n, so that the total increase in the probability that new gates would move into the conducting configuration would be \alpha_{n} (1 - n).
By the same logic, if there was some rate (call it \beta_{n}) at which a gate that is currently conducting would move into a non-conducting configuration, then the probability that gates would move into the non-conducting configuration would be that rate multiplied by the proportion of gates that are currently conducting, which is n, so that the change in probability that new gates would move into the non-conducting configuration would be \beta_{n} n.
So, the total rate of change in the probability of gates conducting would be the probability that some gates became conducting, minus the probability that some became non-conducting, or{\displaystyle 
    \frac{dn}{dt} = \alpha_{n} (1 - n) - \beta_{n} n. \quad\text{(Equation 10)}}
This equation can equivalently be written in a different form, which you will often see. The derivation for the alternative form is here.{\displaystyle 
    \frac{dn}{dt} = \frac{(n_{\infty} -  n)}{\tau_{n}}. \quad\text{(Equation 11)}}
Equation 11 is mathematically identical to Equation 10, but can be thought of conceptually as saying that, at any given voltage, there is a value of the probability of the gating variable n which will be reached if the voltage is held fixed for a very long time (i.e., n_{\infty}), and the rate of change of the probability n will go to zero once this value is reached. The rate at which n reaches this steady-state value depends on a time constant, \tau_{n}. If the time constant is large, it will take the gating variable a long time to reach its steady-state value; if the time constant is small, the gating variable will reach its steady-state value quickly.
We are almost done. We need a way of describing how the time constants change with voltage.
The key idea is that the probabilities of opening or closing are related to the voltage across the membrane.
Hodgkin and Huxley assumed that a change of a gating element is like a chemical reaction, and that the rate relationships could be thought of as illustrated in the following equation, using k_{1} to represent that rate at which the gating elements move from the closed to the open configuration, and k_{-1} to represent the rate at which the gating elements move from the open to the closed configuration:{\displaystyle 
    \text{Closed} \overset{k_{1}}{\underset{k_{-1}}{\rightleftharpoons}} \text{Open}. \quad\text{(Equation 12)}}
At equilibrium, the rate of opening will become equal to the rate of closing, so that the equilibrium constant K will be{\displaystyle 
    K = \frac{k_{1}}{k_{-1}}. \quad\text{(Equation 13)}}
At constant temperature and pressure, which is a reasonable set of conditions to assume for channel gating processes, one can define the energy available for a reaction to occur, also known as the Gibbs energy. At equilibrium, thermodynamic arguments show that{\displaystyle 
    \Delta G^\circ = - RT \ln \ K, \quad\text{(Equation 14)}}where \Delta G^\circ is the Gibbs energy under standard conditions (i.e., fixed temperature and pressure), R is the universal gas constant, T is the absolute temperature, and K is the equilibrium constant we defined in Equation 13.
Now the Gibbs energy has two components: that due to the chemical reaction that allows the ion channel to shift from an open to a closed configuration, and an electrical component due to the voltage field across the membrane, and the charges on the part of the channel that induce it to respond to that field. Thus,{\displaystyle 
    \Delta G^\circ = \Delta G_\text{chem} + \Delta G_\text{elec} = \Delta G_\text{chem} + zFV_{m}, \quad\text{(Equation 15)}}where z is the charge on the ion channel, V_{m} is the voltage across the membrane, and F is Faraday's constant. Combining Equations 14 and 15, and solving for K, we obtain{\displaystyle 
    K = e^{-\tfrac{\Delta G^\circ}{RT}} =  e^{-\tfrac{\Delta G_\text{chem} + \Delta G_\text{elec}}{RT}}

                    = e^{-\frac{\Delta G_\text{chem} + zFV_{m}}{RT}}

                    = e^{-\tfrac{\Delta G_\text{chem}}{RT}} e^{-\tfrac{zFV_{m}}{RT}}}
If we define K_{o} as e^{-\tfrac{\Delta G_\text{chem}}{RT}}, then this simplifies to{\displaystyle 
    K = K_{o} e^{\tfrac{-zFV_{m}}{RT}}. \quad\text{(Equation 16)}}
These considerations were the basis for the actual equations that Hodgkin and Huxley used to fit the data they had obtained for the voltage dependence of the rate constants. Thus, for example, for the rate constant \alpha_{n} describing the rate at which the n gating variable went from the closed to the open configuration as a function of voltage, they used the equation{\displaystyle 
    \alpha_{n}(V_{m}) = \frac {-(V_{m} - V_{2})} {V_{1} \left(e^\tfrac{-(V_{m} - V_{2})}{V_{3}} - 1\right)}, \quad\text{(Equation 17)}}where V_{1}, V_{2}, and V_{3} were parameters that allowed them to shift the center of the curve and alter its sharpness, which they fit to their data.
There was another equation for the rate constant \beta_{n}, describing the rate at which the n gating variable went from the open to the closed configuration as a function of voltage:{\displaystyle 
    \beta_{n}(V_{m}) = V_{4} e^\tfrac{-(V_{m} - V_{5})}{V_{6}}, \quad\text{(Equation 18)}}where V_{4}, V_{5}, and V_{6} were again parameters fit from their data.
The same logic led to two additional differential equations for the m and h gating variables,{\displaystyle 
    \frac{dm}{dt} = \alpha_{m} (1 - m) - \beta_{m} m, \quad\text{(Equation 19)}}and{\displaystyle 
    \frac{dh}{dt} = \alpha_{h} (1 - h) - \beta_{h} h. \quad\text{(Equation 20)}}
Of course, each of the four rate constants for Equations 19 and 20 were also voltage dependent, leading to these four equations:{\displaystyle 
    \alpha_{m}(V_{m}) = \frac {-(V_{m} - V_{8})} {V_{7} \left(e^\tfrac{-(V_{m} - V_{8})}{V_{9}} - 1\right)}, \quad\text{(Equation 21)}}{\displaystyle 
    \beta_{m}(V_{m}) = V_{10} e^\tfrac{-(V_{m} - V_{11})}{V_{12}}, \quad\text{(Equation 22)}}{\displaystyle 
    \alpha_{h}(V_{m}) = V_{13} e^\tfrac{-(V_{m} - V_{14})}{V_{15}}, \quad\text{(Equation 23)}}{\displaystyle 
    \beta_{h}(V_{m}) = \frac {1} {V_{16} \left(e^\tfrac{-(V_{m} - V_{17})}{V_{18}} + 1\right)}. \quad\text{(Equation 24)}}
So the key equations for the Hodgkin and Huxley model are Equations 9 and 10, and 17 through 24. A list of the parameters for the model is here.
Given this information, you could type in the Hodgkin and Huxley equations, and their parameters, into your favorite differential equation solver (e.g., MATLAB, Mathematica), and obtain action potentials.
![Hodgkin Huxley for Single neuron-Yahya Ashrafi](https://user-images.githubusercontent.com/66359010/138996125-60b59bad-1444-45fa-ae5e-3129211247f1.png)



# Hodgkin and Huxley model for Single neuron
    import numpy as np
    from scipy.integrate import odeint
    import pylab as plt

# constants
    vr = -65.0
    C=1.0
    Iext = 10.0
    gNa=120.0
    gK= 36.0
    gL= 0.03
    vNa= 50.0
    vK= -77.0 
    vL= -54.4
    v0 = -65.0
    n0 = 0.31768111085600037
    m0 = 5.2934208791209428E-002
    h0 = 0.59610933633356666  
    x0 = [v0, n0, m0, h0]
    t = np.linspace(0, 100, 10001)

# functions

    def alpha_n(vr,v):
        return (0.1-0.01*(v-vr))/(np.exp(1.0-0.1*(v-vr))-1.0)
    def alpha_m(vr,v):
        return (2.5-0.1*(v-vr))/(np.exp(2.5-0.1*(v-vr))-1.0)
    def alpha_h(vr,v):
        return 0.07 * np.exp((vr-v)/20.0)
    def beta_n(vr,v):
        return 0.125*np.exp((vr-v)/80.0)
    def beta_m(vr,v):
        return  4.0 * np.exp((vr-v)/18.0)
    def beta_h(vr,v):
        return 1.0 / ( 1.0 + np.exp( 3.0 -0.1*(v-vr) ))

    def odesys(x, t, C, Iext, gNa, gK, gL, vNa, vK, vL):
        v,n,m,h = x
    
# loop 
    
    dvdt= (Iext - gNa *m*m*m*h*(v-vNa) - gK *n*n*n*n*(v-vK) - gL*((v-vL))/C)
    dndt= alpha_n(vr,v)*(1.0-n) -beta_n(vr,v)*n
    dmdt= alpha_m(vr,v)*(1.0-m) -beta_m(vr,v)*m
    dhdt= alpha_h(vr,v)*(1.0-h) -beta_h(vr,v)*h
    
    
    
    dxdt = [dvdt, dndt , dmdt , dhdt]
    return dxdt


sol = odeint(odesys, x0, t, args=(C, Iext, gNa, gK, gL, vNa, vK, vL))

# plots

    plt.figure(figsize=(20,20))
    plt.subplot(3, 1, 1)
    plt.xlabel('Time')
    plt.ylabel('Voltage for single Neuron')
    plt.plot(t, sol[:, 0], 'crimson', label='v(t)')
    plt.legend(loc='upper right')

    plt.subplot(3, 1, 2)
    plt.xlabel('Time')
    plt.ylabel('Gates')
    plt.plot(t, sol[:, 1], 'tomato', label='n(t)')
    plt.plot(t, sol[:, 2], 'seagreen', label='m(t)')
    plt.plot(t, sol[:, 3], 'slategrey', label='h(t)')
    plt.legend(loc='upper right')

    plt.subplot(3, 1, 3)
    plt.xlabel('Time')
    plt.ylabel('Gates')
    plt.plot(sol[:, 1], sol[:, 0], 'tomato', label='n(t)')
    plt.plot(sol[:, 2], sol[:, 0], 'seagreen', label='m(t)')
    plt.plot(sol[:, 3], sol[:, 0], 'slategrey', label='h(t)')
    plt.legend(loc='upper right')

![Hodgkin Huxley for Single neuron-Yahya Ashrafi](https://user-images.githubusercontent.com/66359010/138996125-60b59bad-1444-45fa-ae5e-3129211247f1.png)



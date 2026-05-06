# Thermal-hydraulic functions
- Friction factor [-] using Blasius (1913) correlation.
  - `FF.BLA1913(Re [-])`                
- Friction factor [-] using Colebrook (1939) correlation.
  - `FF.COB1939(Re [-], Roughness [m], Equivalent diameter [m])`
- Friction factor [-] using Haaland (1983) correlation.
  - `FF.HAL1983(Re [-], Roughness [m], Equivalent diameter [m])`

- Example:
```
val = FF.BLA1913(600000.0)   
val = FF.COB1939(600000.0,2.0e-6,4.5e-3)
val = FF.HAL1983(600000.0,2.0e-6,4.5e-3)
```
- After the update:
```
val = FF.BL1913(600000.0) = 0.0113540099380335
val = FF.CB1939(600000.0,2.0e-6,4.5e-3) = 0.017145201316443
val = FF.HL1983(600000.0,2.0e-6,4.5e-3) = 0.0170729699917028
```
- Grashoff number (Gr) [-] = rho^2 * g * beta * (Tw - T) * L^3 / (mu^2)
  - `NU.GR(Rho [kg/m^3], Beta [1/K], T_wall [K], T_bulk [K], length [m], mu [Pa-s])`
- Channel Grashoff number (Gr') [-] = rho^2 * g * beta * (Tw - Tin) * t_ch^3 * k / (mu^2)
  - `NU.GR_P(Rho [kg/m^3], Beta [1/K], T_wall [K], T_inlet [K], thickness [m], mu [Pa-s], k [W/m/K])`
- Modified Channel Grashoff number (Gr*) [-] = rho^2 * g * beta * q * t_ch^4 / (mu^2 * k)
  - `NU.GR_S(Rho [kg/m^3], Beta [1/K], q [W/m^2], thickness [m], mu [Pa-s], k [W/m/K])`
- Rayleigh number (Ra) [-] = Gr * Pr
  - `NU.RA(Gr [-], Pr [-])` 
- Channel Rayleigh number (Ra') [-] = Gr_p * Pr * t_ch / L_ch
  - `NU.RA_P(Gr_p [-], Pr [-], thickness [m], length [m])` 
- Modified Channel Rayleigh number (Ra'') [-] = Gr_s * Pr * t_ch / L_ch
  - `NU.RA_PP(Gr_s [-], Pr [-], thickness [m], length [m])`
- Nusselt number [-] by Dittus-Boelter (1930)
  - `NU.DBO1930(Re [-], Pr [-])`
- Nusselt number [-] by Petukhov (1970) - eq. (50) of Petukhov (1970)
  - `NU.PET1970(Re [-], Pr [-])`
- Nusselt number [-] by Gnielinski (1975) - eq. (14) of Gnielinski (1975)
  - `NU.GNI1975(Re [-], Pr [-], Pr_wall [-], eq. diameter [m], length [m])`
- Nusselt number [-] by Churchill and Chu (1975) for Uniform Wall Heat Flux
  - `NU.CHU_UQ1975(Ra [-], Pr [-])` - eq. (14) of Churchill-Chu (1975)
- Nusselt number [-] by Churchill and Chu (1975) for Uniform Wall Temperature
  - `NU.CHU_UT1975(Ra [-], Pr [-])` - eq. (9) of Churchill-Chu (1975)
- Nusselt number [-] by Bar-Cohen and Rohsenow (1984) for Uniform Wall Fluxv (below 4 are from Table 1 of Bar-Cohen and Rohsenow (1984))
  - `NU.BAR_UQ1984(Ra_pp [-])`
- Nusselt number [-] by Bar-Cohen and Rohsenow (1984) for Uniform Wall Flux (Asymmetric)
  - `NU.BAR_HQAS1984(Ra_pp [-])`
- Nusselt number [-] by Bar-Cohen and Rohsenow (1984) for Uniform Wall Temperature
  - `NU.BAR_UT1984(Ra_p [-])`
- Nusselt number [-] by Bar-Cohen and Rohsenow (1984) for Uniform Wall Temperature (Asymmetric)
  - `NU.BAR_UTAS1984(Ra_p [-])`
- Example:
```
L_ch = 1.0
t_ch = 0.003
De = 0.005
q = 1.0e4
V = 2.0
Tin = 300.0
Tb = 310.0
Tw = 320.0
P = 1.0e5
rho = H2O.rho(P,Tb)
beta = H2O.alpha(P,Tb)
mu = H2O.mu(P,Tb)
k = H2O.k(P,Tb)
// Non-dimensional number
Pr = H2O.Pr(P,Tb)
Prw = H2O.Pr(P,Tw)
Re = rho*V*De/mu
Gr = NU.GR(rho,beta,Tw,Tb,L_ch,mu)
Gr_p = NU.GR_P(rho,beta,Tw,Tin,t_ch,mu,k)
Gr_s = NU.GR_S(rho,beta,q,t_ch,mu,k)
Ra = NU.RA(Gr,Pr)
Ra_p = NU.RA_P(Gr_p,Pr,t_ch,L_ch)
Ra_pp = NU.RA_PP(Gr_s,Pr,t_ch,L_ch)
// Nu calculation
Nu = NU.DBO1930(Re, Pr)
Nu = NU.PET1970(Re, Pr)
Nu = NU.GNI1975(Re, Pr, Prw, De, L_ch)
Nu = NU.CHU_UQ1975(Ra, Pr)
Nu = NU.CHU_UT1975(Ra, Pr)
Nu = NU.BAR_UQ1984(Ra_pp)
Nu = NU.BAR_HQAS1984(Ra_pp)
Nu = NU.BAR_UT1984(Ra_p)
Nu = NU.BAR_UTAS1984(Ra_p)
```
- After the update:
```
L_ch = 1.0 = 1
t_ch = 0.003 = 0.003
De = 0.005 = 0.005
q = 1.0e4 = 10000
V = 2.0 = 2
Tin = 300.0 = 300
Tb = 310.0 = 310
Tw = 320.0 = 320
P = 1.0e5 = 100000
rho = H2O.rho(P,Tb) = 993.389265413433
beta = H2O.alpha(P,Tb) = 0.000360304560889208
mu = H2O.mu(P,Tb) = 0.000693330303264211
k = H2O.k(P,Tb) = 0.624515440056194
// Non-dimensional number
Pr = H2O.Pr(P,Tb) = 4.63918083423602
Prw = H2O.Pr(P,Tw) = 3.7839834426511
Re = rho*V*De/mu = 14327.7924062534
Gr = NU.GR(rho,beta,Tw,Tb,L_ch,mu) = 72535230605.7917
Gr_p = NU.GR_P(rho,beta,Tw,Tin,t_ch,mu,k) = 2446.16605891309
Gr_s = NU.GR_S(rho,beta,q,t_ch,mu,k) = 9407.85976170656
Ra = NU.RA(Gr,Pr) = 336504051633.279
Ra_p = NU.RA_P(Gr_p,Pr,t_ch,L_ch) = 34.0446200936048
Ra_pp = NU.RA_PP(Gr_s,Pr,t_ch,L_ch) = 130.934288093068
// Nu calculation
Nu = NU.DBO1930(Re, Pr) = 89.7940956761305
Nu = NU.PET1970(Re, Pr) = 96.4059211255421
Nu = NU.GNI1975(Re, Pr, Prw, De, L_ch) = 98.6207080248506
Nu = NU.CHU_UQ1975(Ra, Pr) = 956.707569513029
Nu = NU.CHU_UT1975(Ra, Pr) = 948.831531230906
Nu = NU.BAR_UQ1984(Ra_pp) = 1.66862183150823
Nu = NU.BAR_HQAS1984(Ra_pp) = 1.78647683536542
Nu = NU.BAR_UT1984(Ra_p) = 1.00536430928435
Nu = NU.BAR_UTAS1984(Ra_p) = 1.27346321583685
```
- Critical Heat Flux (CHF) [W/m^2] using AECL LUT 2006 (without correction parameters).
  - Applicable ranges (100 kPa < p (pressure) < 21,000 kPa; 
    - 0 kg/m^2/s < G (mass flux) < 8,000 kg/m^2/s; 0.5 < X (quality) < 1.0)
  - `CHF.AECL06(p [Pa],  G [kg/m^2/s], X [-])`                        
- Example:
```
p1 = 101.0e3
G1 = 100.0
x1 = -0.5
val1 = CHF.AECL06(p1,G1,x1)
p1 = 300.0e3
G1 = 6000.0
x1 = 0.9
val1 = CHF.AECL06(p1,G1,x1)
```
- After the update:
```
p1 = 101.0e3 = 101000
G1 = 100.0 = 100
x1 = -0.5 = -0.5
val1 = CHF.AECL06(p1,G1,x1) = 8390140
p1 = 300.0e3 = 300000
G1 = 6000.0 = 6000
x1 = 0.9 = 0.9
val1 = CHF.AECL06(p1,G1,x1) = 121000
```
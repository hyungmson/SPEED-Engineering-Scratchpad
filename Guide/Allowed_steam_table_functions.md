# Allowed steam table functions
Following IAPWS-IF97 functions can be used (case-sensitive).
- Properties in regions 1 (subcooled) and 2 (vapor) and 4 (saturated) are available.
- Applicable pressure ranges are: 0.000611~16.529 MPa
- For example, "ps1 = H2O.psat(300.0)" calculates saturation pressure in Pa, corresponding to temperature 300.0K, and stores the value to variable "ps1".       
  - H2O.psat(T [K]) : saturation pressure [Pa]
  - H2O.Tsat(p [Pa]) : saturation temperature [K]
  - H2O.Pr(p [Pa], T [K]) : Pr
  - H2O.Pr_liq(p [Pa], T [K]) : liquid Pr
  - H2O.Pr_vap(p [Pa], T [K]) : vapor Pr
  - H2O.k(p [Pa], T [K]) : thermal conductivity [W/m-K]
  - H2O.k_liq(p [Pa], T [K]) : liquid thermal conductivity [W/m-K]  
  - H2O.k_vap(p [Pa], T [K]) : vapor thermal conductivity [W/m-K] 
  - H2O.cp(p [Pa], T [K]) : isobaric specific heat [J/kg-K] 
  - H2O.cp_liq(p [Pa], T [K]) : liquid isobaric specific heat [J/kg-K]  
  - H2O.cp_vap(p [Pa], T [K]) : vapor isobaric specific heat [J/kg-K] 
  - H2O.cv(p [Pa], T [K]) : isochoric specific heat [J/kg-K] 
  - H2O.cv_liq(p [Pa], T [K]) : liquid isochoric specific heat [J/kg-K]  
  - H2O.cv_vap(p [Pa], T [K]) : vapor isochoric specific heat [J/kg-K] 
  - H2O.mu(p [Pa], T [K]) : dynamic viscosity [Pa-s] 
  - H2O.mu_liq(p [Pa], T [K]) : liquid dynamic viscosity [Pa-s] 
  - H2O.mu_vap(p [Pa], T [K]) : vapor dynamic viscosity [Pa-s]                     
  - H2O.nu(p [Pa], T [K]) : specific volume [m^3/kg]
  - H2O.nu_liq(p [Pa], T [K]) : liquid specific volume [m^3/kg] 
  - H2O.nu_vap(p [Pa], T [K]) : vapor specific volume [m^3/kg]                 
  - H2O.rho(p [Pa], T [K]) : density [kg/m^3]
  - H2O.rho_liq(p [Pa], T [K]) : liquid density [kg/m^3] 
  - H2O.rho_vap(p [Pa], T [K]) : vapor density [kg/m^3]
  - H2O.u(p [Pa], T [K]) : specific internal energy [J/kg]
  - H2O.u_liq(p [Pa], T [K]) : liquid specific internal energy [J/kg]
  - H2O.u_vap(p [Pa], T [K]) : vapor specific internal energy [J/kg]
  - H2O.h(p [Pa], T [K]) : specific enthalpy [J/kg]
  - H2O.h_liq(p [Pa], T [K]) : liquid specific enthalpy [J/kg]
  - H2O.h_vap(p [Pa], T [K]) : vapor specific enthalpy [J/kg]
  - H2O.s(p [Pa], T [K]) : specific entropy [J/K]
  - H2O.s_liq(p [Pa], T [K]) : liquid specific entropy [J/kg/K]
  - H2O.s_vap(p [Pa], T [K]) : vapor specific entropy [J/kg/K]  
  - H2O.w(p [Pa], T [K]) : speed of sound [m/s]
  - H2O.w_liq(p [Pa], T [K]) : liquid speed of sound [m/s]
  - H2O.w_vap(p [Pa], T [K]) : vapor speed of sound [m/s]    
  - H2O.alpha(p [Pa], T [K]) : isobaric cubic expansion coefficient [1/K]
  - H2O.alpha_liq(p [Pa], T [K]) : liquid isobaric cubic expansion coefficient [1/K]
  - H2O.alpha_vap(p [Pa], T [K]) : vapor isobaric cubic expansion coefficient [1/K]  
  - H2O.kappa(p [Pa], T [K]) : isothermal compressibility [1/Pa]
  - H2O.kappa_liq(p [Pa], T [K]) : liquid isothermal compressibility [1/Pa]
  - H2O.kappa_vap(p [Pa], T [K]) : vapor isothermal compressibility [1/Pa]                    
  - H2O.sig(T [K]) : surface tension [N/m]                
  - H2O.T(p [Pa], h [J/kg]) : temperature [K]
  - H2O.T_liq(p [Pa], h [J/kg]) : liquid temperature [K]
  - H2O.T_vap(p [Pa], h [J/kg]) : vapor temperature [K]
  - H2O.Xe_pT(p [Pa], T [K]) : equilibrium quality [-]
  - H2O.Xe_ph(p [Pa], h [J/kg]) : equilibrium quality [-]                    
  - H2O.Reg_pT(p [Pa], T [K]) : region finder (1:liquid, 2:vapor, 4: saturated)
  - H2O.Reg_ph(p [Pa], h [J/kg]) : region finder (1:liquid, 2:vapor, 4: saturated)
  - H2O.k_ph(p [Pa], h [J/kg]) : thermal conductivity [W/m-K]
  - H2O.cp_ph(p [Pa], h [J/kg]) : isobaric specific heat [J/kg-K] 
  - H2O.cv_ph(p [Pa], h [J/kg]) : isochoric specific heat [J/kg-K] 
  - H2O.mu_ph(p [Pa], h [J/kg]) : dynamic viscosity [Pa-s] 
  - H2O.nu_ph(p [Pa], h [J/kg]) : specific volume [m^3/kg]
  - H2O.rho_ph(p [Pa], h [J/kg]) : density [kg/m^3]
  - H2O.u_ph(p [Pa], h [J/kg]) : specific internal energy [J/kg]
  - H2O.s_ph(p [Pa], h [J/kg]) : specific entropy [J/kg/K]
  - H2O.w_ph(p [Pa], h [J/kg]) : speed of sound [m/s]
  - H2O.alpha_ph(p [Pa], h [J/kg]) : isobaric cubic expansion coefficient [1/K]
  - H2O.kappa_ph(p [Pa], h [J/kg]) : isothermal compressibility [1/Pa]
  - H2O.sig_ph(p [Pa], h [J/kg]) : surface tension [N/m]

- Example:
```
// Region 1, Table 2.5 of Wagner and Kretzschmar (2008)
p1 = 3.0e6
T1 = 300.0
val1 = H2O.nu(p1,T1)
val1 = H2O.nu_liq(p1,T1)
val1 = H2O.h(p1,T1)
val1 = H2O.h_liq(p1,T1)
val1 = H2O.u(p1,T1)
val1 = H2O.u_liq(p1,T1)
val1 = H2O.s(p1,T1)
val1 = H2O.s_liq(p1,T1)
val1 = H2O.cp(p1,T1)
val1 = H2O.cp_liq(p1,T1)
val1 = H2O.cv(p1,T1)
val1 = H2O.cv_liq(p1,T1)
val1 = H2O.w(p1,T1)
val1 = H2O.w_liq(p1,T1)
val1 = H2O.alpha(p1,T1)
val1 = H2O.alpha_liq(p1,T1)
val1 = H2O.kappa(p1,T1)
val1 = H2O.kappa_liq(p1,T1)
val1 = H2O.rho(p1,T1)
val1 = H2O.rho_liq(p1,T1)
// Region 2, Table 2.11 of Wagner and Kretzschmar (2008)
p1 = 0.0035e6
T1 = 300.0
val1 = H2O.nu(p1,T1)
val1 = H2O.nu_vap(p1,T1)
val1 = H2O.h(p1,T1)
val1 = H2O.h_vap(p1,T1)
val1 = H2O.u(p1,T1)
val1 = H2O.u_vap(p1,T1)
val1 = H2O.s(p1,T1)
val1 = H2O.s_vap(p1,T1)
val1 = H2O.cp(p1,T1)
val1 = H2O.cp_vap(p1,T1)
val1 = H2O.cv(p1,T1)
val1 = H2O.cv_vap(p1,T1)
val1 = H2O.w(p1,T1)
val1 = H2O.w_vap(p1,T1)
val1 = H2O.alpha(p1,T1)
val1 = H2O.alpha_vap(p1,T1)
val1 = H2O.kappa(p1,T1)
val1 = H2O.kappa_vap(p1,T1)
val1 = H2O.rho(p1,T1)
val1 = H2O.rho_vap(p1,T1)
// Region 4, Table 2.20 of Wagner and Kretzschmar (2008)
T1 = 300.0
T2 = 500.0
T3 = 600.0
val1 = H2O.psat(T1)
val1 = H2O.psat(T2)
val1 = H2O.psat(T3)
p1 = 0.1e6
p2 = 1.0e6
p3 = 10.0e6
val1 = H2O.Tsat(p1)
val1 = H2O.Tsat(p2)
val1 = H2O.Tsat(p3)
// Backward equation for Region 1, Table 2.32 of Wagner and Kretzschmar (2008)
p1 = 3.0e6
h1 = 500.0e3
val1 = H2O.T(p1,h1)
val1 = H2O.T_liq(p1,h1)
val1 = H2O.Reg_ph(p1,h1)
val1 = H2O.k_ph(p1,h1)
val1 = H2O.cp_ph(p1,h1)
val1 = H2O.cv_ph(p1,h1)
val1 = H2O.mu_ph(p1,h1)
val1 = H2O.nu_ph(p1,h1)
val1 = H2O.rho_ph(p1,h1)
val1 = H2O.u_ph(p1,h1)
val1 = H2O.s_ph(p1,h1)
val1 = H2O.w_ph(p1,h1)
val1 = H2O.alpha_ph(p1,h1)
val1 = H2O.kappa_ph(p1,h1)
val1 = H2O.sig_ph(p1,h1)
// Backward equation for Region 2, Table 2.38 of Wagner and Kretzschmar (2008)
p1 = 3.0e6
h1 = 3000.0e3
val1 = H2O.T(p1,h1)
val1 = H2O.T_vap(p1,h1)
val1 = H2O.Reg_ph(p1,h1)
val1 = H2O.k_ph(p1,h1)
val1 = H2O.cp_ph(p1,h1)
val1 = H2O.cv_ph(p1,h1)
val1 = H2O.mu_ph(p1,h1)
val1 = H2O.nu_ph(p1,h1)
val1 = H2O.rho_ph(p1,h1)
val1 = H2O.u_ph(p1,h1)
val1 = H2O.s_ph(p1,h1)
val1 = H2O.w_ph(p1,h1)
val1 = H2O.alpha_ph(p1,h1)
val1 = H2O.kappa_ph(p1,h1)
val1 = H2O.sig_ph(p1,h1)
```
- After the update:
```
// Region 1, Table 2.5 of Wagner and Kretzschmar (2008)
p1 = 3.0e6 = 3000000
T1 = 300.0 = 300
val1 = H2O.nu(p1,T1) = 0.00100215167968669
val1 = H2O.nu_liq(p1,T1) = 0.00100215167968669
val1 = H2O.h(p1,T1) = 115331.273021438
val1 = H2O.h_liq(p1,T1) = 115331.273021438
val1 = H2O.u(p1,T1) = 112324.817982378
val1 = H2O.u_liq(p1,T1) = 112324.817982378
val1 = H2O.s(p1,T1) = 392.294792402624
val1 = H2O.s_liq(p1,T1) = 392.294792402624
val1 = H2O.cp(p1,T1) = 4173.01218406778
val1 = H2O.cp_liq(p1,T1) = 4173.01218406778
val1 = H2O.cv(p1,T1) = 4121.20160358744
val1 = H2O.cv_liq(p1,T1) = 4121.20160358744
val1 = H2O.w(p1,T1) = 1507.73920966903
val1 = H2O.w_liq(p1,T1) = 1507.73920966903
val1 = H2O.alpha(p1,T1) = 0.000277354533426614
val1 = H2O.alpha_liq(p1,T1) = 0.000277354533426614
val1 = H2O.kappa(p1,T1) = 4.46382122802193E-10
val1 = H2O.kappa_liq(p1,T1) = 4.46382122802193E-10
val1 = H2O.rho(p1,T1) = 997.852940098482
val1 = H2O.rho_liq(p1,T1) = 997.852940098482
// Region 2, Table 2.11 of Wagner and Kretzschmar (2008)
p1 = 0.0035e6 = 3500
T1 = 300.0 = 300
val1 = H2O.nu(p1,T1) = 39.491386637763
val1 = H2O.nu_vap(p1,T1) = 39.491386637763
val1 = H2O.h(p1,T1) = 2549911.45084002
val1 = H2O.h_vap(p1,T1) = 2549911.45084002
val1 = H2O.u(p1,T1) = 2411691.59760785
val1 = H2O.u_vap(p1,T1) = 2411691.59760785
val1 = H2O.s(p1,T1) = 8522.38966733579
val1 = H2O.s_vap(p1,T1) = 8522.38966733579
val1 = H2O.cp(p1,T1) = 1913.00162098344
val1 = H2O.cp_vap(p1,T1) = 1913.00162098344
val1 = H2O.cv(p1,T1) = 1441.32661897478
val1 = H2O.cv_vap(p1,T1) = 1441.32661897478
val1 = H2O.w(p1,T1) = 427.920172263105
val1 = H2O.w_vap(p1,T1) = 427.920172263105
val1 = H2O.alpha(p1,T1) = 0.00337578289436129
val1 = H2O.alpha_vap(p1,T1) = 0.00337578289436129
val1 = H2O.kappa(p1,T1) = 0.000286239651391886
val1 = H2O.kappa_vap(p1,T1) = 0.000286239651391886
val1 = H2O.rho(p1,T1) = 0.0253219774016182
val1 = H2O.rho_vap(p1,T1) = 0.0253219774016182
// Region 4, Table 2.20 of Wagner and Kretzschmar (2008)
T1 = 300.0 = 300
T2 = 500.0 = 500
T3 = 600.0 = 600
val1 = H2O.psat(T1) = 3536.58941301301
val1 = H2O.psat(T2) = 2638897.75627322
val1 = H2O.psat(T3) = 12344314.5783766
p1 = 0.1e6 = 100000
p2 = 1.0e6 = 1000000
p3 = 10.0e6 = 10000000
val1 = H2O.Tsat(p1) = 372.755918611338
val1 = H2O.Tsat(p2) = 453.035632391467
val1 = H2O.Tsat(p3) = 584.149487998528
// Backward equation for Region 1, Table 2.32 of Wagner and Kretzschmar (2008)
p1 = 3.0e6 = 3000000
h1 = 500.0e3 = 500000
val1 = H2O.T(p1,h1) = 391.798508762426
val1 = H2O.T_liq(p1,h1) = 391.798508762426
val1 = H2O.Reg_ph(p1,h1) = 1
val1 = H2O.k_ph(p1,h1) = 0.68501917017909
val1 = H2O.cp_ph(p1,h1) = 4237.00783557588
val1 = H2O.cv_ph(p1,h1) = 3671.25070487314
val1 = H2O.mu_ph(p1,h1) = 0.000235607158671144
val1 = H2O.nu_ph(p1,h1) = 0.00105754768641481
val1 = H2O.rho_ph(p1,h1) = 945.5838378221
val1 = H2O.u_ph(p1,h1) = 496854.971126904
val1 = H2O.s_ph(p1,h1) = 1510.68430781112
val1 = H2O.w_ph(p1,h1) = 1529.29558552907
val1 = H2O.alpha_ph(p1,h1) = 0.00084414063380324
val1 = H2O.kappa_ph(p1,h1) = 5.21869978400271E-10
val1 = H2O.sig_ph(p1,h1) = 0.0552401312612472
// Backward equation for Region 2, Table 2.38 of Wagner and Kretzschmar (2008)
p1 = 3.0e6 = 3000000
h1 = 3000.0e3 = 3000000
val1 = H2O.T(p1,h1) = 575.373370238485
val1 = H2O.T_vap(p1,h1) = 575.373370238485
val1 = H2O.Reg_ph(p1,h1) = 2
val1 = H2O.k_ph(p1,h1) = 0.0479025959876757
val1 = H2O.cp_ph(p1,h1) = 2530.43864388663
val1 = H2O.cv_ph(p1,h1) = 1793.57799648275
val1 = H2O.mu_ph(p1,h1) = 2.00864133307093E-05
val1 = H2O.nu_ph(p1,h1) = 0.0816103153931177
val1 = H2O.rho_ph(p1,h1) = 12.2533529638133
val1 = H2O.u_ph(p1,h1) = 2755158.42674638
val1 = H2O.s_ph(p1,h1) = 6551.03209971725
val1 = H2O.w_ph(p1,h1) = 562.038026824322
val1 = H2O.alpha_ph(p1,h1) = 0.00239160732194294
val1 = H2O.kappa_ph(p1,h1) = 3.64493006010993E-07
val1 = H2O.sig_ph(p1,h1) = 0.0138513894189618
```

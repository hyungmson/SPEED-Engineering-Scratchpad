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

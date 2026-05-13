# Fluid properties (PropsSI wrapper of CoolProp 7.2.1dev)
- To use this feature, CoolProp.dll need to be placed where SPEED executable resides.
  - Only compatible with CoolProp.dll provided with SPEED program.
  - Installed automatically when installed from Microsoft Store or Google Play Store.
- Grammar: `FLUID.PROP({output property name},{input property#1 name},{input property#1 value},{input property#2 name},{input property#2 value},{fluid name})`
  - Property name and fluid name follow that of CoolProp.
  - Variable names cannot be same as property names inside the function.
- for fluid names, see below or: [link](https://coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids)
```
//ref.: https://coolprop.org/fluid_properties/PurePseudoPure.html#list-of-fluids
1-Butene,Acetone,Air,Ammonia,Argon,Benzene,
CarbonDioxide,CarbonMonoxide,CarbonylSulfide,CycloHexane,CycloPropane,Cyclopentane,
D4,D5,D6,Deuterium,Dichloroethane,DiethylEther,DimethylCarbonate,DimethylEther,
Ethane,Ethanol,EthylBenzene,Ethylene,EthyleneOxide,Fluorine,HFE143m,
HeavyWater,Helium,Hydrogen,HydrogenChloride,HydrogenSulfide,
IsoButane,IsoButene,Isohexane,Isopentane,Krypton,
MD2M,MD3M,MD4M,MDM,MM,Methane,Methanol,
MethylLinoleate,MethylLinolenate,MethylOleate,MethylPalmitate,MethylStearate,
Neon,Neopentane,Nitrogen,NitrousOxide,Novec649,
OrthoDeuterium,OrthoHydrogen,Oxygen,
ParaDeuterium,ParaHydrogen,Propylene,Propyne,
R11,R113,R114,R115,R116,R12,R123,R1233zd(E),R1234yf,R1234ze(E),R1234ze(Z),R124,
R1243zf,R125,R13,R1336mzz(E),R134a,R13I1,R14,R141b,R142b,R143a,R152A,R161,
R21,R218,R22,R227EA,R23,R236EA,R236FA,R245ca,R245fa,R32,R365MFC,
R40,R404A,R407C,R41,R410A,R507A,RC318,
SES36,SulfurDioxide,SulfurHexafluoride,Toluene,Water,Xenon,
cis-2-Butene,m-Xylene,n-Butane,n-Decane,n-Dodecane,n-Heptane,n-Hexane,n-Nonane,
n-Octane,n-Pentane,n-Propane,n-Undecane,o-Xylene,p-Xylene,trans-2-Butene
```
- for property (parameter) names, see below or: [link](https://coolprop.org/coolprop/HighLevelAPI.html#parameter-table)
```
//ref.: https://coolprop.org/coolprop/HighLevelAPI.html#parameter-table
// name : definition [units] - can be used for input or output
DELTA, Delta : Reduced density (rho/rhoc) [] - Input/Output
DMOLAR, Dmolar : Molar density [mol/m^3] - Input/Output
D, DMASS, Dmass : Mass density [kg/m^3] - Input/Output
HMOLAR, Hmolar : Molar specific enthalpy [J/mol] - Input/Output
H, HMASS, Hmass : Mass specific enthalpy [J/kg] - Input/Output
P : Pressure [Pa] - Input/Output
Q : Molar vapor quality [mol/mol] - Input/Output
SMOLAR, Smolar : Molar specific entropy [J/mol/K] - Input/Output
S, SMASS, Smass : Mass specific entropy [J/kg/K] - Input/Output
TAU, Tau : Reciprocal reduced temperature (Tc/T) [] - Input/Output
T : Temperature [K] - Input/Output
UMOLAR, Umolar : Molar specific internal energy [J/mol] - Input/Output
U, UMASS, Umass : Mass specific internal energy [J/kg] - Input/Output
ACENTRIC, acentric : Acentric factor [] - Output only
ALPHA0, alpha0 : Ideal Helmholtz energy [] - Output only
ALPHAR, alphar : Residual Helmholtz energy [] - Output only
A, SPEED_OF_SOUND, speed_of_sound : Speed of sound [m/s] - Output only
BVIRIAL, Bvirial : Second virial coefficient [] - Output only
CONDUCTIVITY, L, conductivity : Thermal conductivity [W/m/K] - Output only
CP0MASS, Cp0mass : Ideal gas mass specific constant pressure specific heat [J/kg/K] - Output only
CP0MOLAR, Cp0molar : Ideal gas molar specific constant pressure specific heat [J/mol/K] - Output only
CPMOLAR, Cpmolar : Molar specific constant pressure specific heat [J/mol/K] - Output only
CVIRIAL, Cvirial : Third virial coefficient [] - Output only
CVMASS, Cvmass, O : Mass specific constant volume specific heat [J/kg/K] - Output only
CVMOLAR, Cvmolar : Molar specific constant volume specific heat [J/mol/K] - Output only
C, CPMASS, Cpmass : Mass specific constant pressure specific heat [J/kg/K] - Output only
D2ALPHA0_DDELTA2_CONSTTAU, d2alpha0_ddelta2_consttau : Second derivative of ideal Helmholtz energy with delta [] - Output only
D3ALPHA0_DDELTA3_CONSTTAU, d3alpha0_ddelta3_consttau : Third derivative of ideal Helmholtz energy with delta [] - Output only
DALPHA0_DDELTA_CONSTTAU, dalpha0_ddelta_consttau : Derivative of ideal Helmholtz energy with delta [] - Output only
DALPHA0_DTAU_CONSTDELTA, dalpha0_dtau_constdelta : Derivative of ideal Helmholtz energy with tau [] - Output only
DALPHAR_DDELTA_CONSTTAU, dalphar_ddelta_consttau : Derivative of residual Helmholtz energy with delta [] - Output only
DALPHAR_DTAU_CONSTDELTA, dalphar_dtau_constdelta : Derivative of residual Helmholtz energy with tau [] - Output only
DBVIRIAL_DT, dBvirial_dT : Derivative of second virial coefficient with respect to T [] - Output only
DCVIRIAL_DT, dCvirial_dT : Derivative of third virial coefficient with respect to T [] - Output only
DIPOLE_MOMENT, dipole_moment : Dipole moment [C m] - Output only
FH : Flammability hazard [] - Output only
FRACTION_MAX, fraction_max : Fraction (mole, mass, volume) maximum value for incompressible solutions [] - Output only
FRACTION_MIN, fraction_min : Fraction (mole, mass, volume) minimum value for incompressible solutions [] - Output only
FUNDAMENTAL_DERIVATIVE_OF_GAS_DYNAMICS, fundamental_derivative_of_gas_dynamics : Fundamental derivative of gas dynamics [] - Output only
GAS_CONSTANT, gas_constant : Molar gas constant [J/mol/K] - Output only
GMOLAR_RESIDUAL, Gmolar_residual : Residual molar Gibbs energy [J/mol] - Output only
GMOLAR, Gmolar : Molar specific Gibbs energy [J/mol] - Output only
GWP100 : 100-year global warming potential [] - Output only
GWP20 : 20-year global warming potential [] - Output only
GWP500 : 500-year global warming potential [] - Output only
G, GMASS, Gmass : Mass specific Gibbs energy [J/kg] - Output only
HELMHOLTZMASS, Helmholtzmass : Mass specific Helmholtz energy [J/kg] - Output only
HELMHOLTZMOLAR, Helmholtzmolar : Molar specific Helmholtz energy [J/mol] - Output only
HH : Health hazard [] - Output only
HMASS_IDEALGAS, Hmass_idealgas : Ideal gas specific enthalpy [J/kg] - Output only
HMOLAR_IDEALGAS, Hmolar_idealgas : Ideal gas molar enthalpy [J/mol] - Output only
HMOLAR_RESIDUAL, Hmolar_residual : Residual molar enthalpy [J/mol] - Output only
ISENTROPIC_EXPANSION_COEFFICIENT, isentropic_expansion_coefficient : Isentropic expansion coefficient [] - Output only
ISOBARIC_EXPANSION_COEFFICIENT, isobaric_expansion_coefficient : Isobaric expansion coefficient [1/K] - Output only
ISOTHERMAL_COMPRESSIBILITY, isothermal_compressibility : Isothermal compressibility [1/Pa] - Output only
I, SURFACE_TENSION, surface_tension : Surface tension [N/m] - Output only
M, MOLARMASS, MOLAR_MASS, MOLEMASS, molar_mass, molarmass, molemass : Molar mass [kg/mol] - Output only
ODP : Ozone depletion potential [] - Output only
PCRIT, P_CRITICAL, Pcrit, p_critical, pcrit : Pressure at the critical point [Pa] - Output only
PHASE, Phase : Phase index as a float [] - Output only
PH : Physical hazard [] - Output only
PIP : Phase identification parameter [] - Output only
PMAX, P_MAX, P_max, pmax : Maximum pressure limit [Pa] - Output only
PMIN, P_MIN, P_min, pmin : Minimum pressure limit [Pa] - Output only
PRANDTL, Prandtl : Prandtl number [] - Output only
PTRIPLE, P_TRIPLE, p_triple, ptriple : Pressure at the triple point (pure only) [Pa] - Output only
P_REDUCING, p_reducing : Pressure at the reducing point [Pa] - Output only
RHOCRIT, RHOMASS_CRITICAL, rhocrit, rhomass_critical : Mass density at critical point [kg/m^3] - Output only
RHOMASS_REDUCING, rhomass_reducing : Mass density at reducing point [kg/m^3] - Output only
RHOMOLAR_CRITICAL, rhomolar_critical : Molar density at critical point [mol/m^3] - Output only
RHOMOLAR_REDUCING, rhomolar_reducing : Molar density at reducing point [mol/m^3] - Output only
SMASS_IDEALGAS, Smass_idealgas : Ideal gas specific entropy [J/kg/K] - Output only
SMOLAR_IDEALGAS, Smolar_idealgas : Ideal gas molar entropy [J/mol/K] - Output only
SMOLAR_RESIDUAL, Smolar_residual : Residual molar entropy (sr/R = s(T,rho) - s^0(T,rho)) [J/mol/K] - Output only
TCRIT, T_CRITICAL, T_critical, Tcrit : Temperature at the critical point [K] - Output only
TMAX, T_MAX, T_max, Tmax : Maximum temperature limit [K] - Output only
TMIN, T_MIN, T_min, Tmin : Minimum temperature limit [K] - Output only
TTRIPLE, T_TRIPLE, T_triple, Ttriple : Temperature at the triple point [K] - Output only
T_FREEZE, T_freeze : Freezing temperature for incompressible solutions [K] - Output only
T_REDUCING, T_reducing : Temperature at the reducing point [K] - Output only
UMASS_IDEALGAS, Umass_idealgas : Ideal gas specific internal energy [J/kg] - Output only
UMOLAR_IDEALGAS, Umolar_idealgas : Ideal gas molar internal energy [J/mol] - Output only
V, VISCOSITY, viscosity : Viscosity [Pa s] - Output only
Z : Compressibility factor [] - Output only
```
- Example:
```
pp = 101325
qq = 0
(FLUID.PROP(T,P,pp,Q,qq,Water))
sig = FLUID.PROP(I,P,101325,Q,0,HeavyWater)
```
- After the update:
```
pp = 101325 = 101325
qq = 0 = 0
(FLUID.PROP(T,P,pp,Q,qq,Water)) = 373.124295847666
sig = FLUID.PROP(I,P,101325,Q,0,HeavyWater) = 0.0586588999934768
```

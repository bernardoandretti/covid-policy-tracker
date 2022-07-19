### Key changes

On 25 July 2022 the OxCGRT implemented data changes which incorporate different policies applying to vaccinated and non-vaccinated people. We now publish two different types of csv in our main data repo: `latest` csvs (which contain a summary selection of our data), and `differentiated with notes csvs (which contain almost all of our data). The structure and contents of these are detailed below:


## Main csv files
**In the main `latest` csv files**, a summary of the key changes to the data structure is below:

- **Indicators**: 
  - 9 indicators now report ‘M’ majority value (C1-7, H6-8; e.g. ‘C1M_School closing’) to reflect V or NV policy where differentiation. C1, C2, C3, C4, C5, C6, C7, H6 and H8 are now reported with a capital M in the end (e.g., as ‘C1M’) to summarise the differentiated values. If no differentiation is in place, the value applying to everyone is reported. If differentiation is in place, this reports the policy applying to the **Majority** of people using vaccination rates- if under 50% vaccinated, NV value reported, if over 50% reported, V value reported.
    <br> This majority "M" column ensures a continuous series of data for these nine indicators. In sum, this reports:
    <br> - **Everyone value**: if no differentiation in place 
    <br> - **Non-vaccinated value**: if majority population (over 50%) are non-vaccinated
    <br> - **Vaccinated value**: if majority population (over 50%) are vaccinated

  - C8EV - International travel now reports the vaccinated (V) value if there are differentiated policies in place, and everyone (E) value if there is no differentiation.
    <br> - Note that this indicator reports policies applying to international arrivals, NOT the domestic population. 
    <br> - This is different to our previous method, where we reported the non-vaccinated policy for C8, so historical revisions to C8 values will be noted.
    
 | Indicators | Majority* | Population Vaccinated |
 | --- | --- | ---|
  | `C1M`, `C2M`, `C3M`, `C4M`, `C5M`, `C6M`, `C7M`, `H6M`, `H8M` | Reports either E value if no differentiation, or the V or NV value if differentiated policies are in place, depending on which proportion of population are V or NV | Reports: <br> - % people vaccinated, except for India and China subnational data  <br> - ‘MV’ (Majority Vaccinated) for China and India subnational data  <br> - ‘MNV’ (Majority Non-Vaccinated) for China and India subnational data |
  |`C8EV` | Reports either E value if no differentiation, or the vaccinated value V | Reports: <br> - % people vaccinated, except for India and China subnational data  <br> - ‘MV’ (Majority Vaccinated) for China and India subnational data  <br> - ‘MNV’ (Majority Non-Vaccinated) for China and India subnational data |


- **Indices**:

  - Stringency, Government Response, and Containment and Health indices take on the ‘Average’ value (e.g. ‘SI_Average’) . Values in the ‘Average’ column can report either:
    <br> - Everyone (E) value from indicators if no differentiation
    <br> - Weighted average if there are differentiated (V/NV) policies, weighted by % national/subnational level vaccination data whenever available (reported in ‘Population vaccinated’ column)
    <br> - Simple average value if there is differentiation and no % vaccination data available. Note this only applies for India and China subnational data.

 |  | Government Response Index | Containment and Health Index | Stringency Index | Explanation |
 | --- | --- | ---| --- | ---|
  | Average | GRI_Average | CHI_Average | SI_Average | Reports: <br> -  Everyone value from indicators if no differentiation <br> - Weighted average if there are differentiated policies and good % vaccination data <br> -  Simple average value if there is differentiation and no % vaccination data available. Note this only applies for India and China subnational data |


## Full withnotes csv files

**In the full `withnotes csv files**, a summary of the key changes to the data structure is below:

This contains the full raw data and everyone (E), non-vaccinated (NV), and vaccinated (V) values for the 10 indicators with differentiated coding, as well as four versions of the Stringency Index, Government Response Index, and Containment and Health Index.

Per indicator:
- **Everyone** (e.g. C1E_School closing)
- **Non-vaccinated** (e.g. C1NV_School closing)
- **Vaccinated** (e.g. C1V_School closing)
- **Majority** (as described above) (e.g. C1M_School closing)

 | Indicators | Everyone (E) | Non-vaccinated (NV)| Vaccinated (V)| Majority(M)*| Population vaccinated|
 | --- | --- | ---| --- | --- | ---|
 |`C1`, `C2`, `C3`, `C4`, `C5`, `C6`, `C7`, `C8`, `H6`, `H8` | Value applying to everyone if no differentiated policy | Policy applying to non-vaccinated people | Policy applying to vaccinated people | Reports either E value if no differentiated policy, or the V (50% or more of population vaccinated) or NV (50% or more of population non-vaccinated) value if differentiated policy | Reports: <br> - % people vaccinated, except for India and China subnational data  <br> - ‘MV’ (Majority Vaccinated) for China and India subnational data  <br> - ‘MNV’ (Majority Non-Vaccinated) for China and India subnational data |
 
 *Note: reporting the Majority value means that sometimes an indicator value will change due to the % vaccinated value crossing the 50% value, meaning the V value is reported, not the NV value. To explain this, we add the below note to the ‘differentiated withnotes’ file:

- "On this date the proportion of people vaccinated became greater than 50%. The policy reported is now the one applying to vaccinated people, not non-vaccinated people as was previously reported."


- **Indices**:

The full `withnotes csv files report four different versions of each index:


 |  | Non-vaccinated | Vaccinated | Simple Average | Weighted Average |
 | --- | --- | ---| --- | ---| 
  | Explanation | Uses `non-vaccinated` policy if present, `everyone` policy if not | Uses `vaccinated` policy if present, `everyone` policy if not | Sum of `non-vaccinated` and `vaccinated` policies/ 2 | Weights index value by the proportion of vaccinated population using `non-vaccinated` and `vaccinated values (not available for China and India subnational data) | 
  | Government Response Index | `GRI_Nonvax` | `GRI_Vax` | `GRI_SimpleAverage` | `GRI_WeightedAverage` |
  | Containment and Health Index | `CHI_Nonvax` | `CHI_Vax` | `CHI_SimpleAverage` | `CHI_WeightedAverage` |
  | Stringency Index | `SI_Nonvax` | `SI_Vax` | `SI_SimpleAverage` | `SI_WeightedAverage` |






The GRI, SI, and CHI now report an `Average index value. Where population vaccination data are available (% of fully vaccinated people) this is a **Weighted Average**. Where no vaccination data are available, we instead create a dummy that indicates whether the majority of the population is either vaccinated (MV) or non-vaccinated (MNV),  and report a **Simple Average** of the V and NV values.
- Please note that we report simple averages only for India and China subnational jurisdictions.



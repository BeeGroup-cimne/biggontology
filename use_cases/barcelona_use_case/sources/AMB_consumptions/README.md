# AMB Consumptions description

The AMB (Barcelona Metropolitan Area) data provides detailed information on gas and electricity consumption for each
cadastral reference in Barcelona, covering the entire year of 2017. It includes gas and electricity consumption,
measured in kWh/m². It offers an accurate view of energy use throughout the city for that year.

## Gathering tool

This data source comes in the format of an XLSX file where there are columns that contains consumptions for a cadastral
reference.

#### RUN import application

To run the import application, execute the python script with the following parameters:

```bash
python3 -m gather -so AMB_consumptions -f <file> -n <namespace> -u <user_importing> -tz <file_timezone> -st <storage>
```

## Raw Data Format

The information is stored in a graph database called Neo4j, where all data is linked and harmonized according to the
BIGG ontology. Time series data will be stored in an Hbase table, with each endpoint providing different types of
information, each having its own row key.

#### AMB Consumptions

````json
{
  "OBJECTID": 46,
  "CODI_INE": 8019,
  "ParcelaID": 118476,
  "Municipi": "BARCELONA",
  "CODIMT": 2,
  "CODIMTI": 2,
  "CODIMTIP": 1639,
  "codisecc": "0801905001",
  "REFCAT": "5069821DF2856G",
  "F14Cat": "UNIFAMILIARS IRREGULARS",
  "F4Cat": "UNIFAMILIARS",
  "Codi_Teix": "UI108",
  "ASR": "Mixtura de classes intermèdies",
  "Us_princ": "Residencial",
  "Num_elem": 6.0,
  "Num_viv": 1.0,
  "Sup_finca": 439.0,
  "Sup_cons": 138.0,
  "V306_SCT.Scons.total": 114,
  "V313_ssr": 114,
  "BR_V_M2": 49.0,
  "V313_V306": 1.0,
  "BR_V_V313": 0.4298245614035088,
  "anypond": 1960.0,
  "TU_ampCarr": 5.59429349503,
  "TU_alcadMa": 5.11,
  "TU_FARscsr": 0.376237623762,
  "TU_BCR": 0.194522067638,
  "TU_UCRmean": 0.74272113247,
  "TU_RSD": 0.831351288731,
  "PobEstim11": 0.856682906679,
  "AlcadaPond": 4.94957055361,
  "Compactnes": 1.05549279761,
  "CertMitja": " ",
  "FIL_1_>80_SCR": "Aplica",
  "FIL_2_>66_BR_V": "No aplica",
  "FIL_3_C_EL": "Aplica",
  "FIL_4_TIP_F14": "Aplica",
  "FIL_5_TARIFA": "Aplica",
  "XARXA DE GAS": "sí",
  "XARXA DE DH": "sí",
  "TEC_1_N_SUBMIN": 2,
  "TEC_1_CUENTA_0": nan,
  "TEC_1_CUENTA_1": nan,
  "TEC_1_CUENTA_2": 1.0,
  "SUB_ENER": "ELECTRICITAT+GAS",
  "G_N_CUPS_GBL": nan,
  "G_SUM_GBL": nan,
  "E_N_CUPS_TOT": nan,
  "E_SUM_TOT": 7690.0,
  "CEE_SUP_CONS": 50.94,
  "CEE_HAB_CER": 1.0,
  "CEE_QUAL_PRO": 0,
  "CEE_FONT_ACS": "Gas",
  "CEE_FONT_CAL": nan,
  "CEE_FONT_REF": nan,
  "TEC3_INST": "Només ACS",
  "TEC3_NO_CAL": "sí",
  "TEC3_CAL": nan,
  "TEC3_REFR": nan,
  "SuperfCo": 5.32,
  "FVA_Superf": 5.32,
  "FVA_PotIns": 0.78,
  "FVA_Produc": 657.17,
  "FVB_Superf": 5.32,
  "FVB_PotIns": 0.78,
  "FVB_Produc": 657.17,
  "TEC2_PrFVB_SSR": 5.764649122807017,
  "S_ARQ_SIM": "H",
  "S_SOL_CONS": "C2",
  "S_EST_METEOCAT": "BCN",
  "CLI_HVAC": "HV4",
  "CLI_CONC": "HC2BCNHV1",
  "FIS_EF_E_SUP": nan,
  "FIS_EF_G_SUP": nan,
  "FIS_EF_TOT_SUP": nan,
  "FIS_EP_E_SUP": nan,
  "FIS_EP_G_SUP": nan,
  "FIS_EP_TOT_SUP": nan,
  "FE_POTC": nan,
  "FG_CON": nan,
  "FIS_HVAC_LLINDA 1": "HV4",
  "FIS_CONC_LL1": "HC2BCNHV4",
  "Total electricitat (kWh/m²)": 18.665944,
  "Total gas (kWh/m²)": 16.03964,
  "Total EF (kWh/m²)": 34.705584,
  "EPNR electricitat (kWh/m²)": 44.200955392,
  "EPNR gas (kWh/m²)": 19.1673698,
  "EPNR total (kWh/m²)": 63.368325192,
  "FE_€_TOTAL": 518.0487290260048,
  "FG_€_TOTAL": 258.06390688572384,
  "ENERGIA_€_TOTAL": 776.1126359117286,
  "ENERGIA_€_SUP": 5.229869514229977
}
````

## Harmonization

The harmonization of the data will be done with the following [mapping](sources/AMB_consumptions/mapping.yaml):

#### Classes=>

| Ontology classes    | URI format                                    | Transformation actions |
|---------------------|-----------------------------------------------|------------------------|
| saref:Device        | namespace#Device&lt;deviceId&gt;              |                        |
| saref:Measurement   | namespace#&lt;id&gt;                          |                        |
| saref:UnitOfMeasure | namespace#unit-kWh/m2                         |                        |
| saref:Property      | namespace#Property&lt;measurementTypology&gt; |                        |

#### Relations=>

| Origin class      | Destination class   | Relation               |
|-------------------|---------------------|------------------------|
| saref:Measurement | saref:UnitOfMeasure | saref:isMeasuredIn     |
| saref:Measurement | s4bldg:Building     | saref:isMeasurementOf  |
| saref:Measurement | saref:Property      | saref:controlsProperty |
| saref:Device      | saref:Measurement   | saref:makesMeasurement |






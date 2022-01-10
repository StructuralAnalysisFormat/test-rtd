# StructuralLoadCombination

**Load Combination**

Object serves for definition a load combination. The combination is created from the existing load cases in the model, in [StructuralLoadCase](structuralloadcase.md) sheet.

## Specification in the excel

| Column header| Data type | Example / enum definition | Required | Description |
| :---------------------------: | :--------------: | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|              Name             |      String      |                                                                                                                                                                                                          COM1                                                                                                                                                                                                         |                                                                      yes                                                                      | Human readable unique name of the object                                                                                                                                                                                                                                                                                                                                                                                                                 |
|          Description          |      String      |                                                                                                                                                                                                varibale\_1 + dead load                                                                                                                                                                                                |                                                                       no                                                                      | The description of the load combination                                                                                                                                                                                                                                                                                                                                                                                                                  |
|            Category           |       Enum       |                                                                                                              <p>ULS (Ultimate Limit State)</p><p></p><p>SLS (Serviceability Limit State)</p><p></p><p>ALS (Accidental Limit State)</p><p></p><p>According national standard</p><p></p><p>Not defined</p>                                                                                                              |                                                                      yes                                                                      | The category of the load combination                                                                                                                                                                                                                                                                                                                                                                                                                     |
|       National standard       |       Enum       | <p>EN-ULS(STR/GEO) Set B</p><p></p><p>EN-ULS (STR/GEO) Set C</p><p></p><p>EN-Accidental 1</p><p></p><p>EN-Accidental 2</p><p></p><p>EN-Seismic<br></p><p>EN-SLS</p><p>Characteristic</p><p></p><p>EN-SLS Frequent</p><p></p><p>EN-SLS Quasi-permanent</p><p></p><p>IBC-LRFD ultimate</p><p></p><p>IBC-ASD ultimate</p><p></p><p>IBC-ASD serviceability</p><p></p><p>IBC-ASD seismic</p><p></p><p>IBC-LRFD seismic</p> |                                                 yes, If Category =According national standard                                                 | The National code application                                                                                                                                                                                                                                                                                                                                                                                                                            |
|              Type             |       Enum       |                                                                                                                                                                                            <p>Envelope<br></p><p>Linear</p>                                                                                                                                                                                           | <p>no, optional for Categories:<br><br>ULS (Ultimate Limit State)</p><p></p><p>SLS (Serviceability Limit State)<br><br>Not defined</p><p></p> | <p>Distinguish between linear and envelope combination.</p><p></p><p>In case combination type is linear, the exact content of combination is presented.</p><p></p><p>In case combination is the envelope, all [StructuralLoadCase](structuralloadcase.md) are presented. Linear combinations can be composed based on relations defined in[StrucutralLoadGroup](structuralloadgroup.md).</p> |
|         Load factor #         |      double      |                                                                                                                                                                                                          1,35                                                                                                                                                                                                         |                                             yes, If Category in not "According national standard"                                             | Load factor of the load case. # means indexing of the Load factor column, e.g. Load factor 1, Load factor 2, … Load factor 99. It depends on how many load case is considered in combination.                                                                                                                                                                                                                                                            |
|          Multiplier #         |      double      |                                                                                                                                                                                                          0,9                                                                                                                                                                                                          |                                                                      yes                                                                      | A multiplier for e.g. increase the selfweight of the structure . # means indexing of the Multiplier column, e.g. Multiplier 1, Multiplier 2, … Multiplier 99. It depends on how many load case is considered in combination.                                                                                                                                                                                                                             |
|        Load case name #       |      String      |                                                                                                                                                                                                          LC1                                                                                                                                                                                                          |                                                                      yes                                                                      | Valid name of the load case ([StructuralLoadCase](structuralloadcase.md)). # means indexing of the load case name column, e.g. Load case name 1, Load case name 2, … load case name 99. It depends on how many load case is considered in combination.                                                                                                                                                                                         |
|               Id              |      String      |                                                                                                                                                                                          39f238a5-01d0-45cf-a2eb-958170fd4f39                                                                                                                                                                                         |                                                                       no                                                                      | Unique attribute designation                                                                                                                                                                                                                                                                                                                                                                                                                             |
# RelConnectsRigidCross

**Rigid Cross**

RigidCross is defining structural behavior of node ([StructuralPointConnection](../structural-analysis-elements/structuralpointconnection.md)), where two 1D elements ([StructuralCurveMember](../structural-analysis-elements/structuralcurvemember.md)) are being crossed. 1D members could be independent or dependency could be defined in following excel sheet. Rigid cross is often used for bracing of the structure.

![](../.gitbook/assets/24\_rigidcross.png)

## Specification in the excel

| Column header| Data type | Example / enum definition | Required | Description |
| :---------------------------: | :--------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|              Name             |      String      |                                                                                                       RC1                                                                                                      |                                                                        yes                                                                       | Human readable unique name of the object                                                                                                                                                                                                                                                                                                                                                                                                          |
|           1D Members          |      String      |                                                                                                     B1; B3                                                                                                     | <p>yes</p><p>value from ([StructuralCurveMember](../structural-analysis-elements/structuralcurvemember.md)) | <p>The name from ([StructuralCurveMember](../structural-analysis-elements/structuralcurvemember.md))</p><p>Two 1D members should be defined</p>                                                                                                                                                                                                                                                                  |
|              Type             |       Enum       |                                                                              <p>Fixed</p><p></p><p>Hinged</p><p></p><p>Custom</p>                                                                              |                                                                        no                                                                        | <p>Constraint of the Rigid Cross</p><p>The way the Rigid Cross acts in individual directions. Has informative character.</p><p>When all constraints are set to Rigid = Fixed</p><p>When all constraints are set to Free = Hinge</p><p>Custom allows user defined behavior of Cross link and creating the Coupler</p>                                                                                                                              |
|               u1              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Compression only</p><p></p><p>Tension only</p><p></p><p>Flexible compression only</p><p></p><p>Flexible tension only</p><p></p><p>Non linear</p> |                                                                        yes                                                                       | <p>Displacement of first connected member</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p><p>(Flexible) compression/tension only - acts rigid or flexible, only for defined strain (compression or tension)</p>  |
|               u2              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Compression only</p><p></p><p>Tension only</p><p></p><p>Flexible compression only</p><p></p><p>Flexible tension only</p><p></p><p>Non linear</p> |                                                                        yes                                                                       | <p>Displacement of second connected member</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p><p>(Flexible) compression/tension only - acts rigid or flexible, only for defined strain (compression or tension)</p> |
|               u               |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Compression only</p><p></p><p>Tension only</p><p></p><p>Flexible compression only</p><p></p><p>Flexible tension only</p><p></p><p>Non linear</p> |                                                                        yes                                                                       | <p>Displacement of RigidCross</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p><p>(Flexible) compression/tension only - acts rigid or flexible, only for defined strain (compression or tension)</p>              |
|              fi1              |       Enum       |                                                                  <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Non linear</p>                                                                  |                                                                        yes                                                                       | <p>Rotation for the first connected member</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p>                                                                                                                      |
|              fi2              |       Enum       |                                                                  <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Non linear</p>                                                                  |                                                                        yes                                                                       | <p>Rotation for the second connected member</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p>                                                                                                                     |
|               fi              |       Enum       |                                                                  <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p><p></p><p>Non linear</p>                                                                  |                                                                        yes                                                                       | <p>Rotation for the RigidCross</p><p>Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Non linear - resistance in specified direction could be defined</p>                                                                                                                                  |
|      Stiffness u1 \[MN/m]     |      Double      |                                                                                                       3.0                                                                                                      |                                      yes, if u1 = Flexible, Flexible compression/tension only or Non linear                                      | <p>The flexibility in direction of first member</p><p>Use this property only if the u1 is set Flexible, Flexible compression/tension only or Non linear</p>                                                                                                                                                                                                                                                                                       |
|       Resitance u1 \[MN]      |      Double      |                                                                                                      0.20                                                                                                      |                                                              yes, if u1 = Non linear                                                             | <p>The resistance in direction of first member</p><p>Use this property only if the u1 is set Non linear</p>                                                                                                                                                                                                                                                                                                                                       |
|      Stiffness u2 \[MN/m]     |      Double      |                                                                                                       3.0                                                                                                      |                                      yes, if u2 = Flexible, Flexible compression/tension only or Non linear                                      | <p>The flexibility in direction of second member</p><p>Use this property only if the u2 is set Flexible, Flexible compression/tension only or Non linear</p>                                                                                                                                                                                                                                                                                      |
|       Resitance u2 \[MN]      |      Double      |                                                                                                      0.20                                                                                                      |                                                              yes, if u2 = Non linear                                                             | <p>The resistance in direction of second member</p><p>Use this property only if the u2 is set Non linear</p>                                                                                                                                                                                                                                                                                                                                      |
|      Stiffness u \[MN/m]      |      Double      |                                                                                                       5.0                                                                                                      |                                       yes, if u = Flexible, Flexible compression/tension only or Non linear                                      | <p>The flexibility of the RigidCross</p><p>Use this property only if the u is set Flexible, Flexible compression/tension only or Non linear</p>                                                                                                                                                                                                                                                                                                   |
|       Resitance u \[MN]       |      Double      |                                                                                                      0.35                                                                                                      |                                                              yes, if u = Non linear                                                              | <p>The resistance of the RigidCross</p><p>Use this property only if the u is set Non linear</p>                                                                                                                                                                                                                                                                                                                                                   |
|    Stiffness fi1 \[MNm/rad]   |      Double      |                                                                                                       1.0                                                                                                      |                                                       yes, if fi1 = Flexible or Non linear                                                       | <p>Torsional stiffness around the 1st member</p><p>Use this property only if the fi1 is set Flexible or Non linear</p>                                                                                                                                                                                                                                                                                                                            |
|     Resistance fi1 \[MNm]     |      Double      |                                                                                                      0.05                                                                                                      |                                                             yes, if fi1 = Non linear                                                             | <p>Torsional resistance around the 1st member</p><p>Use this property only if the fi1 is set Non linear</p>                                                                                                                                                                                                                                                                                                                                       |
|    Stiffness fi2 \[MNm/rad]   |      Double      |                                                                                                       1.0                                                                                                      |                                                       yes, if fi2 = Flexible or Non linear                                                       | <p>Torsional stiffness around the 2st member</p><p>Use this property only if the fi2 is set Flexible or Non linear</p>                                                                                                                                                                                                                                                                                                                            |
|     Resistance fi2 \[MNm]     |      Double      |                                                                                                      0.05                                                                                                      |                                                             yes, if fi2 = Non linear                                                             | <p>Torsional resistance around the 2st member</p><p>Use this property only if the fi2 is set Non linear</p>                                                                                                                                                                                                                                                                                                                                       |
|    Stiffness fi \[MNm/rad]    |      Double      |                                                                                                       4.0                                                                                                      |                                                        yes, if fi = Flexible or Non linear                                                       | <p>Torsional stiffness of the RigidCross</p><p>Use this property only if the fi is set Flexible or Non linear</p>                                                                                                                                                                                                                                                                                                                                 |
|      Resistance fi \[MNm]     |      Double      |                                                                                                      0.25                                                                                                      |                                                              yes, if fi = Non linear                                                             | <p>Torsional resistance of the RigidCross</p><p>Use this property only if the fi is set Non linear</p>                                                                                                                                                                                                                                                                                                                                            |
|           Parent ID           |      String      |                                                                                      67b35d84-3d04-47aa-aa4a-dc1263982320                                                                                      |                                                                        no                                                                        | <p>Is filled for objects created be dividing curved geometry to series of straight line objects.<br><br>Parent ID will ensure that curved edge is imported as straight parts to nonsupporting application, and back to original supporting application as curved geometry.</p><p>To ensure successful round trip of segmented objects and their related objects, Parent ID needs to be present in both directions.</p>                            |
|               Id              |      String      |                                                                                      39f238a5-01d0-45cf-a2eb-958170fd4f39                                                                                      |                                                                        no                                                                        | Unique attribute designation                                                                                                                                                                                                                                                                                                                                                                                                                      |

## Notes

>**Resistance** is defined by the value of maximal strain. Until is the value of maximal strain reached, Rigid cross acts fully rigid. After the value exceeded, RigidCross acts flexibly due to defined Value of Stiffness. This is how non linear behavior is achieved.
>
>The axis of the connection is defined by the members of the RigidCross:
>
>* The first axis is assigned to the first member (i.e. the first member selected by the user during the definition of a new RigidCross - column "1D Members").
>* The second axis is assigned to the second member (i.e. the second member selected by the user during the definition of a new RigidCross - column "1D Members").
>* The third axis is perpendicular at the plane defined by member 1 and member 2.
>
>**Non linear** behavior of material is handled with "Resistance". The example is shown below.
>
>```{image} ../.gitbook/assets/25\_rigidlink\_resistance.png
>:width: 500px
>```
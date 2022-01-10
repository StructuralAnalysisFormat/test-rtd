# RelConnectsStructuralMember

**Hinges on 1D member**

The entity RelConnectsStructuralMember allows users to release degrees of freedom between structural members (beams, columns) and structural connection objects (nodes or supports). When no RelConnectsStrucutralMember is defined, connections are taken into account as fully rigid. The defined connections may be rigid or free or anything in between. In each direction (translations along X, Y, and Z local 1D member axes, rotation around X, Y, and Z local 1D member axes) the condition may be: Free, Rigid, Flexible.

![](../.gitbook/assets/22\_relconnectsstructuralmember.png)

## Specification in the excel:

| Column header| Data type | Example / enum definition | Required | Description |
| :---------------------------: | :--------------: | :--------------------------------------------------: | :--------------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|              Name             |      String      |                          H1                          |           yes          | Human readable unique name of the RelConnectsStrucutralMember                                                                                                                                                                                                                                                                                                                                                          |
|             Member            |      String      |                       Beam B54                       |           yes          | The name of the curve member to which is hinge related                                                                                                                                                                                                                                                                                                                                                                 |
|            Position           |       Enum       |    <p>Begin</p><p></p><p>End</p><p></p><p>Both</p>   |           yes          | The position of the hinge on the curve member. \*see notes                                                                                                                                                                                                                                                                                                                                                             |
|               ux              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Translation in X direction. Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                             |
|               uy              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Translation in Y direction. Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                             |
|               uz              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Translation in Z direction. Free - That is it imposes no constraint in the direction. Rigid - The connection in fully rigid in the specified direction. Flexible - The connection is flexible (elastic) in the specified direction. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                             |
|              fix              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Rotational stiffness around X axis. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                                                                                                                                                                                                                             |
|              fiy              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Rotational stiffness around Y axis. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                                                                                                                                                                                                                             |
|              fiz              |       Enum       | <p>Free</p><p></p><p>Rigid</p><p></p><p>Flexible</p> |           yes          | Rotational stiffness around Z axis. Parameter Flexible can be linear only, non-linearity is not supported.                                                                                                                                                                                                                                                                                                             |
|      Stiffness X \[MN/m]      |      Double      |                          100                         |  yes, if ux = Flexible | The flexibility of the connection in X direction                                                                                                                                                                                                                                                                                                                                                                       |
|      Stiffness Y \[MN/m]      |      Double      |                          100                         |  yes, if uy = Flexible | The flexibility of the connection in Y direction                                                                                                                                                                                                                                                                                                                                                                       |
|      Stiffness Z \[MN/m]      |      Double      |                          100                         |  yes, if uz = Flexible | The flexibility of the connection in Z direction                                                                                                                                                                                                                                                                                                                                                                       |
|    Stiffness Fix \[MNm/rad]   |      Double      |                          50                          | yes, if fix = Flexible | The flexibility in rotation of the connection around local X axis                                                                                                                                                                                                                                                                                                                                                      |
|    Stiffness Fiy \[MNm/rad]   |      Double      |                          50                          | yes, if fiy = Flexible | The flexibility in rotation of the connection around local Y axis                                                                                                                                                                                                                                                                                                                                                      |
|    Stiffness Fiz \[MNm/rad]   |      Double      |                          50                          | yes, if fiz = Flexible | The flexibility in rotation of the connection around local Z axis                                                                                                                                                                                                                                                                                                                                                      |
|           Parent ID           |      String      |         67b35d84-3d04-47aa-aa4a-dc1263982320         |           no           | <p>Is filled for objects created be dividing curved geometry to series of straight line objects.<br><br>Parent ID will ensure that curved edge is imported as straight parts to nonsupporting application, and back to original supporting application as curved geometry.</p><p>To ensure successful round trip of segmented objects and their related objects, Parent ID needs to be present in both directions.</p> |
|               Id              |      String      |         39f238a5-01d0-45cf-a2eb-958170fd4f39         |           no           | Unique attribute designation                                                                                                                                                                                                                                                                                                                                                                                           |

## Notes

>**Hinge position** is used for allowing users to define where degrees of freedom are released (user defined constrains).
>
>When the fully rigid connection is desired - no RelConnectsStructuralMember is defined!
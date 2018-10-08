# NSIS_strExplode
NSIS Library used to split a string into an array based on a separator character.

For more information on NSIS please see http://nsis.sourceforge.net

## Expected Warnings
The following warning may be thrown by the NSIS compiler and can be ignored
```
Warning 1  FIXME
```
```
Warning 2 un.  FIXME
```

## Dependancies

## Usage:
strExplode Length Separator String

| Parameter    | Type            | Description                          |
| :---         |      :---:      | :---                                 |
| Length	     | int             | return array count                   |  
| Separator		 | char            | character used to split the string   |
| String			 | string          | string you want split into array     |

 
### Example 1 - Known count of elements returned:
```NSIS
!include strExplode.nsh
strExplode $0 '.' '4.7.1'
${If} $0 == 3
  Pop $1
  Pop $2
  Pop $3
  DetailPrint "First Part: $1"
  DetailPrint "Sectond Part: $2"
  DetailPrint "Third Part: $3"
${EndIf}
```
 
### Example 2 - Unknown count of elements returned:
```NSIS
!include strExplode.nsh
strExplode $0 '.' '4.7.1'
${do}
  Pop $1
  ${If} ${Errors}
    ;All Parts have been popped
    ClearErrors
    ${ExitDo}
  ${Else}
    DetailPrint "Part Value: $1"
  ${EndIf}
${loop}
```

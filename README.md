﻿# vs code settings

## Creating Custom Snippets
1. `crtl+shift+p` 
2. `Preferences: Configure User Snippets`
3. Select the language (eg `mvbasic`)
4. `[language].json` will be created
5. Add the snippets and save
   
## Sample snippets
`mvbasic.json`
```json
{
    "t24subr": {
    "prefix": "t24subr",
    "body": [
        "SUBROUTINE ${TM_FILENAME_BASE}",
        "*------------------------------------------------------------------",
        "* ${CLIPBOARD}",
        "*------------------------------------------------------------------",
        "* Developer: Aaron Niyonzima(aaron@mathisi.io)",
        "* Date     : ${CURRENT_DATE}/${CURRENT_MONTH}/${CURRENT_YEAR}",
        "* Version  : 0.0.1",
        "*-------------------------------------------------------------------",
        "\t$$INSERT I_COMMON",
        "\t$$INSERT I_EQUATE",
        "\t${2:}\n",
        "\tRETURN",
        "END",
    ],
    "description": "T24 Subroutine Template"
    },
    "fread": {
        "prefix": "fread",
        "body": "CALL F.READ(${1:fname}, ${2:id}, ${3:record}, ${4:fh}, err)",
        "description": "Read T24 File record"
    },
    "opf": {
        "prefix": "opf",
        "body": "CALL OPF(${1:fname}, ${2:fh})",
        "description": "Open File"
    },
    "insert": {
        "prefix": "insert",
        "body": "$$INSERT I_F.${1:fname}",
        "description": "Insert File"
    },
    "localref": {
        "prefix": "localref",
        "body": [
            "CALL GET.LOC.REF('${1:IN_APPL}', '${2:IN_FIELD.NAME}', ${3:OUT_POS.NO})",
            "${4:VAR} = ${5:record}<${6:PREX}.LOCAL.REF, ${3:OUT_POS.NO}>"
        ],
        "description": "Get local ref table (eg. ACCOUNT>AC.LOCAL.REF>STAFF.ID"
    }
}
```

## Enable the custom snippet

Add the following lines `settings.json`

```json
...

   "[mvbasic]": {
       "editor.quickSuggestions": {
           "other": true,
           "comments": false,
           "strings": true
       }
   }
   
...
```

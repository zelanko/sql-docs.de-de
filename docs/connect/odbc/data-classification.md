---
title: Verwenden der Datenklassifizierung mit Microsoft ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: 75688cc1e5155c83501204f1634d320b9ae7d8be
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264003"
---
# <a name="data-classification"></a>Datenklassifizierung
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Übersicht
Um sensible Daten zu verwalten, haben SQL Server und Azure SQL Server die Möglichkeit eingeführt, Daten Bank Spalten mit vertraulichen Metadaten bereitzustellen, die es der Client Anwendung ermöglichen, verschiedene Arten von sensiblen Daten (z. b. Integrität, Finanzwesen usw.) zu verarbeiten. ) in Übereinstimmung mit den Datenschutzrichtlinien.

Weitere Informationen zum Zuweisen von Klassifizierungen zu Spalten finden Sie unter [SQL-Daten Ermittlung und-Klassifizierung](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017).

Microsoft ODBC Driver 17,2 ermöglicht das Abrufen dieser Metadaten über SQLGetDescField mithilfe des SQL_CA_SS_DATA_CLASSIFICATION-Feld Bezeichners.

## <a name="format"></a>Format
SQLGetDescField weist die folgende Syntax auf:

```  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```
*DescriptorHandle*  
 Der IRD (Implementierungs Zeilen Deskriptor) handle. Kann durch einen Aufrufen von SQLGetStmtAttr mit dem SQL_ATTR_IMP_ROW_DESC-Anweisungs Attribut abgerufen werden.
  
 *RecNumber*  
 [Eingabe] 0
  
 *FieldIdentifier*  
 Der SQL_CA_SS_DATA_CLASSIFICATION
  
 *ValuePtr*  
 Ausgeben Ausgabepuffer
  
 *BufferLength*  
 Der Länge des Ausgabepuffers in Bytes

 *Stringlengthptr* Ausgeben Ein Zeiger auf den Puffer, in dem die Gesamtzahl der für die Rückgabe in *ValuePtr*verfügbaren Bytes zurückgegeben werden soll.
 
> [!NOTE]
> Wenn die Größe des Puffers unbekannt ist, kann er durch Aufrufen von SQLGetDescField mit *ValuePtr* als NULL und untersuchen des Werts von *stringlengthptr*ermittelt werden.
 
Wenn keine Daten Klassifizierungs Informationen verfügbar sind, wird ein *Ungültiger deskriptorfeldfehler* zurückgegeben.

Bei einem erfolgreichen Aufrufen von SQLGetDescField enthält der Puffer, auf den *ValuePtr* zeigt, die folgenden Daten:

 `nn nn [n sensitivitylabels] tt tt [t informationtypes] cc cc [c columnsensitivitys]`

> [!NOTE]
> `nn nn`, `tt tt`, und `cc cc` sind Multibytezeichen-Ganzzahlen, die mit dem geringsten signifikanten Byte an der niedrigsten Adresse gespeichert werden.

*`sensitivitylabel`* und *`informationtype`* sind beide in der Form.

 `nn [n bytes name] ii [i bytes id]`

*`columnsensitivity`* hat die Form

 `nn nn [n sensitivityprops]`

Für jede Spalte *(c)* sind *n* 4 Byte *`sensitivityprops`* vorhanden:

 `ss ss tt tt`

s-Index in das *`sensitivitylabels`* Array, `FF FF` wenn keine Bezeichnung

t-Index in das *`informationtypes`* Array, `FF FF` wenn keine Bezeichnung


<br><br>
Das Format der Daten kann als die folgenden Pseudo Strukturen ausgedrückt werden:

```
struct IDnamePair {
 BYTE nameLen;
 USHORT name[nameLen];
 BYTE idLen;
 USHORT id[idLen];
};

struct SensitivityProp {
 USHORT labelIdx;
 USHORT infoTypeIdx;
};

USHORT nLabels;
struct IDnamePair labels[nLabels];
USHORT nInfoTypes;
struct IDnamePair infotypes[nInfoTypes];
USHORT nColumns;
struct {
 USHORT nProps;
 struct SensitivityProp[nProps];
} columnClassification[nColumns];
```


## <a name="code-sample"></a>Codebeispiel
Test Anwendung, die das Lesen von Daten Klassifizierungs Metadaten veranschaulicht. Unter Windows kann es mit einer Verbindungs `cl /MD dataclassification.c /I (directory of msodbcsql.h) /link odbc32.lib` Zeichenfolge kompiliert und mit einer SQL-Abfrage ausgeführt werden (die klassifizierte Spalten zurückgibt) als Parameter:

```
#ifdef _WIN32
#include <windows.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include <msodbcsql.h>
#include <stdio.h>
SQLHANDLE env, dbc, stmt;
void checkRC_exit(SQLRETURN rc, SQLHANDLE hand, SQLSMALLINT htype, int retcode, char *action)
{
    if ((rc == SQL_ERROR || rc == SQL_SUCCESS_WITH_INFO) && hand)
    {
        char msg[1024], state[6];
        int i = 0;
        SQLRETURN rc2;
        SQLINTEGER err;
        SQLSMALLINT lenout;
        while ((rc2 = SQLGetDiagRec(htype, hand, ++i, state, &err, msg, sizeof(msg), &lenout)) == SQL_SUCCESS ||
            rc2 == SQL_SUCCESS_WITH_INFO)
            printf("%d (%d)[%s]%s\n", i, err, state, msg);
    }
    if (rc == SQL_ERROR && retcode)
    {
        printf("Error occurred%s%s\n", action ? " upon " : "", action ? action : "");
        exit(retcode);
    }
}
void printLabelInfo(char *type, char **pptr)
{
    char *ptr = *pptr;
    unsigned short nlabels;
    printf("----- %s(%u) -----\n", type, nlabels = *(unsigned short*)ptr);
    ptr += sizeof(unsigned short);
    while (nlabels--)
    {
        int namelen, idlen;
        char *nameptr, *idptr;
        namelen = *ptr++;
        nameptr = ptr;
        ptr += namelen * 2;
        idlen = *ptr++;
        idptr = ptr;
        ptr += idlen * 2;
        wprintf(L"Name: \"%.*s\" Id: \"%.*s\"\n", namelen, nameptr, idlen, idptr);
    }
    *pptr = ptr;
}
int main(int argc, char **argv)
{
    unsigned char *dcbuf;
    unsigned int dclen = 0;
    SQLRETURN rc;
    SQLHANDLE ird;
    if (argc < 3)
    {
        fprintf(stderr, "usage: dataclassification connstr query\n");
        return 1;
    }
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_ENV, 0, &env), 0, 0,
        2, "allocate environment");
    checkRC_exit(SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0), env, SQL_HANDLE_ENV,
        3, "set ODBC version");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc), env, SQL_HANDLE_ENV,
        4, "allocate connection");
    checkRC_exit(SQLDriverConnect(dbc, 0, argv[1], SQL_NTS, 0, 0, 0, SQL_DRIVER_NOPROMPT), dbc, SQL_HANDLE_DBC,
        5, "connect to server");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt), dbc, SQL_HANDLE_DBC,
        6, "allocate statement");
    checkRC_exit(SQLExecDirect(stmt, argv[2], SQL_NTS), stmt, SQL_HANDLE_STMT,
        7, "execute query");
    checkRC_exit(SQLGetStmtAttr(stmt, SQL_ATTR_IMP_ROW_DESC, (SQLPOINTER)&ird, SQL_IS_POINTER, 0), stmt, SQL_HANDLE_STMT,
        8, "get IRD handle");
    rc = SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, 0, &dclen);
    if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
    {
        checkRC_exit(rc, ird, SQL_HANDLE_DESC, 0, 0);
        printf("Error reading SQL_CA_SS_DATA_CLASSIFICATION IRD field. Ensure that the driver and\n"
            "server both support the Data Classification feature, and that the query returns columns\n"
            "with classification information.\n");
    }
    else
    {
        SQLINTEGER dclenout;
        unsigned char *dcptr;
        unsigned short ncols;
        printf("Data Classification information (%u bytes):\n", dclen);
        if (!(dcbuf = malloc(dclen)))
        {
            printf("Memory Allocation Error");
            return 9;
        }
        checkRC_exit(SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, dclen, &dclenout),
            ird, SQL_HANDLE_DESC, 10, "reading SQL_CA_SS_DATA_CLASSIFICATION");
        dcptr = dcbuf;
        printLabelInfo("Labels", &dcptr);
        printLabelInfo("Information Types", &dcptr);
        printf("----- Column Sensitivities(%u) -----\n", ncols = *(unsigned short*)dcptr);
        dcptr += sizeof(unsigned short);
        while (ncols--)
        {
            unsigned short nprops = *(unsigned short*)dcptr;
            dcptr += sizeof(unsigned short);
            while (nprops--)
            {
                unsigned short labelidx, typeidx;
                labelidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                typeidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                printf(labelidx == 0xFFFF ? "(none) " : "%u ", labelidx);
                printf(typeidx == 0xFFFF ? "(none)\n" : "%u\n", typeidx);
            }
            printf("-----\n");
        }
        if (dcptr != dcbuf + dclen)
        {
            printf("Error: unexpected parse of DATACLASSIFICATION data\n");
            return 11;
        }
        free(dcbuf);
    }
    return 0;
}
```


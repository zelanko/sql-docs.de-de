---
title: Zurückgeben von Arrayparametern aus gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 2018069b-da5d-4cee-a971-991897d4f7b5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a154a8739438b76f12e311d0dec0e9d98d886457
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837023"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Zurückgeben von Arrayparametern aus gespeicherten Prozeduren
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 In Oracle 7.3 ist es keine Möglichkeit, einen Datensatztyp PL/SQL, mit Ausnahme von einem PL/SQL-Programm zugreifen. Verfügt eine gepackte Prozedur oder Funktion ein formalen Argument als ein PL/SQL-Datensatztyp definiert, ist es nicht möglich, dieses formale Argument als Parameter zu binden. Verwenden Sie den Typ PL/SQL-Tabelle in der Microsoft ODBC-Treiber für Oracle, zum Aufrufen von Arrayparametern aus Prozeduren, die die richtigen Escapesequenzen enthält.  
  
 Um die Prozedur aufzurufen, verwenden Sie die folgende Syntax:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Die \<Max-Datensätze angefordert >-Parameter muss größer als oder gleich der Anzahl der Zeilen im Resultset vorhanden sein. Andernfalls Oracle einen Fehler, der für dem Benutzer durch den Treiber übergeben wird.  
>   
>  PL/SQL-Datensätze können nicht als Arrayparameter verwendet werden. Jedes Arrayparameter kann nur eine Spalte einer Datenbanktabelle darstellen.  
  
 Das folgende Beispiel definiert ein Paket mit beiden Verfahren, die verschiedenen Resultsets zurückgeben, und klicken Sie dann bietet zwei Möglichkeiten zum Zurückgeben von Resultsets aus dem Paket.  
  
## <a name="package-definition"></a>Paketdefinition:  
  
```  
CREATE OR REPLACE PACKAGE SimplePackage AS  
  
TYPE t_id is TABLE of  NUMBER(5)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Course is TABLE of VARCHAR2(10)  
    INDEX BY BINARY_INTEGER;  
  
TYPE t_Dept is TABLE of VARCHAR2(5)  
    INDEX BY BINARY_INTEGER;  
  
PROCEDURE proc1  
   (  
   o_id             OUT    t_id,  
   ao_course       OUT    t_Course,  
   ao_dept         OUT    t_Dept  
   );  
  
TYPE t_pk1Type1 IS TABLE OF VARCHAR2(100) INDEX BY BINARY_INTEGER;  
TYPE t_pk1Type2 IS TABLE OF NUMBER INDEX BY BINARY_INTEGER;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   );  
  
END SimplePackage;  
  
CREATE OR REPLACE PACKAGE BODY SimplePackage AS  
    PROCEDURE  proc1 ( o_id OUT t_id,  
    ao_course OUT t_Course, ao_dept OUT t_Dept   ) AS  
    BEGIN  
          o_id(1):= 200;  
          ao_course(1) :=  'M101';  
          ao_dept(1) :=  'EEE' ;  
  
          o_id(2) := 201;  
          ao_course(2) :=  'PHY320';  
          ao_dept(2) :=  'ECE' ;  
  
     END proc1;  
PROCEDURE proc2  
   (  
   i_Arg1         IN    NUMBER,  
   ao_Arg2         OUT   t_pk1Type1,  
   ao_Arg3         OUT   t_pk1Type2  
   )  
AS  
   i   NUMBER;  
BEGIN  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg2(i) := 'Row Number ' || to_char(i);  
   END LOOP;  
   FOR i IN 1 .. i_Arg1 LOOP  
      ao_Arg3(i) := i;  
   END LOOP;  
END proc2;  
END SimplePackage;  
```  
  
#### <a name="to-invoke-procedure-proc1"></a>Zum Aufrufen der Prozedur PROC1  
  
1.  Gibt alle Spalten in ein einzelnes Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Jede Spalte als ein einzelnes Resultset zurückgeben:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Dies gibt drei Resultsets, eine für jede Spalte zurück.  
  
#### <a name="to-invoke-procedure-proc2"></a>Zum Aufrufen der Prozedur PROC2  
  
1.  Gibt alle Spalten in ein einzelnes Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Jede Spalte als ein einzelnes Resultset zurückgeben:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Stellen Sie sicher, dass Ihre Anwendungen alle Abrufen der Resultsets mithilfe der [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) API. Weitere Informationen finden Sie in der *ODBC Programmer's Reference*.  
  
> [!NOTE]  
>  In den ODBC-Treiber für Oracle, Version 2.0 können nicht Oracle-Funktionen, die PL/SQL-Arrays zurückgeben verwendet werden, um Resultsets zurückzugeben.

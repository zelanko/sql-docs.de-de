---
title: Zurückgeben von Array Parametern aus gespeicherten Prozeduren | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc998dadc0e0c4a4bfe054bfd1d40296bc176393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292860"
---
# <a name="returning-array-parameters-from-stored-procedures"></a>Zurückgeben von Arrayparametern aus gespeicherten Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 In Oracle 7,3 gibt es keine Möglichkeit, auf einen PL/SQL-Daten Satz Typ außer einem PL/SQL-Programm zuzugreifen. Wenn ein gepacktes Verfahren oder eine Funktion über ein formales Argument verfügt, das als PL/SQL-Datensatz definiert ist, ist es nicht möglich, dieses formale Argument als Parameter zu binden. Verwenden Sie den PL/SQL-Tabellentyp im Microsoft ODBC Driver for Oracle, um Array Parameter aus Prozeduren aufzurufen, die die richtigen Escapesequenzen enthalten.  
  
 Verwenden Sie die folgende Syntax, um die Prozedur aufzurufen:  
  
```  
{call  <package-name>.<proc-or-func>;  
(..., {resultset <max-records-requested> ,<formal-array-param_1>,;  
 <formal-array-param_2>,...,<formal-array-param_n> }, ... ) }  
```  
  
> [!NOTE]  
>  Der \<> Parameter ' Max-Records ' angeforderte Wert muss größer oder gleich der Anzahl der im Resultset vorhandenen Zeilen sein. Andernfalls gibt Oracle einen Fehler zurück, der vom Treiber an den Benutzer übermittelt wird.  
>   
>  PL/SQL-Datensätze können nicht als Array Parameter verwendet werden. Jeder Array Parameter kann nur eine Spalte einer Datenbanktabelle darstellen.  
  
 Im folgenden Beispiel wird ein Paket definiert, das zwei Prozeduren enthält, die unterschiedliche Resultsets zurückgeben und dann zwei Möglichkeiten zur Rückgabe von Resultsets aus dem Paket bereitstellen  
  
## <a name="package-definition"></a>Paket Definition:  
  
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
  
#### <a name="to-invoke-procedure-proc1"></a>So rufen Sie Procedure proc1 auf  
  
1.  Gibt alle Spalten in einem einzelnen Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc1( {resultset  3, o_id , ao_course, ao_dept  } ) }  
    ```  
  
2.  Gibt jede Spalte als einzelnes Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc1( {resultset 3, o_id},  {resultset 3, ao_course}, {resultset 3, ao_dept} ) }  
    ```  
  
     Dies gibt drei Resultsets zurück, jeweils eine für jede Spalte.  
  
#### <a name="to-invoke-procedure-proc2"></a>So rufen Sie Procedure Proc2 auf  
  
1.  Gibt alle Spalten in einem einzelnen Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset  5, ao_Arg2, ao_Arg3} ) }  
    ```  
  
2.  Gibt jede Spalte als einzelnes Resultset zurück:  
  
    ```  
    {call SimplePackage.Proc2( 5 , {resultset 5, ao_Arg2}, {resultset 5, ao_Arg3} ) }  
    ```  
  
 Stellen Sie sicher, dass Ihre Anwendungen alle Resultsets mithilfe der [SQLMoreResults](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) -API abrufen. Weitere Informationen finden Sie in der *ODBC Programmer es Reference*.  
  
> [!NOTE]  
>  Im ODBC-Treiber für Oracle-Version 2,0 können Oracle-Funktionen, die PL/SQL-Arrays zurückgeben, nicht zum Zurückgeben von Resultsets verwendet werden.

---
title: Erstellen eines benutzerdefinierten Datentypalias | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.userdefineddatatype.general.f1
- sql12.swb.new.datatype.properties.general.f1
helpviewer_keywords:
- alias data types [SQL Server], creating
ms.assetid: b1dd8413-0cd0-411b-a79b-1bb043ccc62d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b073e6025bc1483db2482a03d525b758d39efea4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917444"
---
# <a name="create-a-user-defined-data-type-alias"></a>Erstellen eines benutzerdefinierten Datentypalias
  In diesem Thema wird beschrieben, wie ein neuer benutzerdefinierter Datentypalias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]erstellt wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **So erstellen Sie einen benutzerdefinierten Datentypalias mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Bei der Verwendung eines Namens für einen benutzerdefinierten Datentypalias müssen die Regeln für Bezeichner eingehalten werden.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CREATE TYPE-Berechtigung für die aktuelle Datenbank und die ALTER-Berechtigung für *schema_name*. Wenn *schema_name* nicht angegeben wird, gelten die Standardregeln für die Namensauflösung, um das Schema für den aktuellen Benutzer zu bestimmen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-user-defined-data-type"></a>So erstellen Sie einen benutzerdefinierten Datentyp  
  
1.  Erweitern Sie im Objekt-Explorer **Datenbanken**, erweitern Sie eine Datenbank, erweitern Sie **Programmierbarkeit**, erweitern Sie **Typen**, klicken Sie mit der rechten Maustaste auf **Benutzerdefinierte Datentypen**, und klicken Sie dann auf **Neuer benutzerdefinierter Datentyp**.  
  
     **NULL-Werte zulassen**  
     Geben Sie an, ob der benutzerdefinierte Datentyp NULL-Werte akzeptieren kann. Die NULL-Zulässigkeit eines vorhandenen benutzerdefinierten Datentyps ist nicht bearbeitbar.  
  
     **Datentyp**  
     Wählen Sie den Basisdatentyp aus dem Listenfeld aus. Im Listenfeld werden alle Datentypen mit Ausnahme der Datentypen `geography`, `geometry`, `hierarchyid`, `sysname`, `timestamp` und `xml` angezeigt. Der Datentyp eines vorhandenen benutzerdefinierten Datentyps ist nicht bearbeitbar.  
  
     **Standard**  
     Wählen Sie optional eine Regel oder einen Standardwert zum Binden an den benutzerdefinierten Datentypalias aus.  
  
     **Länge/Genauigkeit**  
     Zeigt jeweils die Länge bzw. Genauigkeit des Datentyps an. **Länge** gilt für zeichenbasierte benutzerdefinierte Datentypen, und **Genauigkeit** gilt nur für auf numerischen Werten basierende benutzerdefinierte Datentypen. Die Bezeichnung ändert sich je nach dem zuvor gewählten Datentyp. Dieses Feld ist bearbeitbar, wenn die Länge oder Genauigkeit des ausgewählten Datentyps fest ist.  
  
     Für die Datentypen `nvarchar(max)`, `varchar(max)` oder `varbinary(max)` wird keine Länge angezeigt.  
  
     **Name**  
     Wenn Sie einen neuen benutzerdefinierten Datentypalias erstellen, geben Sie einen eindeutigen Namen ein, der in der gesamten Datenbank verwendet werden soll, um den benutzerdefinierten Datentyp darzustellen. Die maximale Anzahl von Zeichen muss dem System `sysname` Datentyp entsprechen. Der Name eines vorhandenen benutzerdefinierten Datentypalias ist nicht bearbeitbar.  
  
     **Regel**  
     Wählen Sie optional eine Regel zum Binden an den benutzerdefinierten Datentypalias aus.  
  
     **Skalieren**  
     Gibt an, wie viele Dezimalstellen (Ziffern nach dem Dezimalzeichen) maximal gespeichert werden können.  
  
     **Schema**  
     Wählen Sie ein Schema aus einer Liste mit allen für den aktuellen Benutzer verfügbaren Schemas aus. Die Standardauswahl ist das Standardschema für den aktuellen Benutzer.  
  
     **Storage**  
     Zeigt die maximale Speichergröße für den benutzerdefinierten Datentypalias an. Die maximalen Speicherplatzgrößen variieren in Abhängigkeit von der Genauigkeit.  
  
    |||  
    |-|-|  
    |1 – 9|5|  
    |10 – 19|9|  
    |20 – 28|13|  
    |29 – 38|17|  
  
     Bei `nchar` den `nvarchar` Datentypen und ist der Speicher Wert immer das Zweifache des Werts in **Länge**.  
  
     Für die Datentypen `nvarchar(max)`, `varchar(max)` oder `varbinary(max)` wird kein Speicher angezeigt.  
  
2.  Geben Sie im Dialogfeld **Neuer benutzerdefinierter Datentyp** in das Feld **Schema** das Schema ein, das diesen Datentypalias besitzen soll, oder wählen Sie mit der Schaltfläche zum Durchsuchen das Schema aus.  
  
3.  Geben Sie in das Feld **Name** einen Namen für den neuen Datentypalias ein.  
  
4.  Wählen Sie im Feld **Datentyp** den Datentyp aus, auf dem der neue Datentypalias basieren soll.  
  
5.  Vervollständigen Sie, soweit für diesen Datentyp zutreffend, die Felder **Länge**, **Genauigkeit**und **Dezimalstellen** .  
  
6.  Aktivieren Sie **NULL-Werte zulassen** , damit der neue Datentypalias NULL-Werte zulässt.  
  
7.  Vervollständigen Sie im Bereich **Bindung** die Felder **Standard** oder **Regel** , falls Sie dem neuen Datentypalias einen Standardwert oder eine Regel zuordnen möchten. Standardwerte und Regeln können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]nicht erstellt werden. Verwenden Sie [!INCLUDE[tsql](../../includes/tsql-md.md)]. Beispielcode zum Erstellen von Standardwerten und Regeln finden Sie im Vorlagen-Explorer.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-user-defined-data-type-alias"></a>So erstellen Sie einen benutzerdefinierten Datentypalias  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird ein Datentypalias erstellt, der auf dem vom System bereitgestellten Datentyp `varchar` basiert. Der Datentypalias `ssn` wird für Spalten mit elfstelligen Sozialversicherungsnummern verwendet (999-99-9999). Diese Spalte darf nicht den Wert NULL aufweisen.  
  
```sql  
CREATE TYPE ssn  
FROM varchar(11) NOT NULL ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankbezeichner](database-identifiers.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)  
  
  

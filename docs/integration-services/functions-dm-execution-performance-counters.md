---
title: dm_execution_performance_counters (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 1b38e8e3-c560-4b6e-b60e-bfd7cfcd4fdf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 543a4502199287432ca8a13220fa95223797340a
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65724036"
---
# <a name="functions---dmexecutionperformancecounters"></a>Funktionen – dm_execution_performance_counters

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Gibt die Leistungsstatistik für eine Ausführung zurück, die auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
dm_execution_performance_counters [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @execution_id = ] *execution_id*  
 Der eindeutige Bezeichner der Ausführung, die ein oder mehrere Pakete enthält. Die Ausführung von Paketen mit dem Task "Paket ausführen" erfolgt in der gleichen Ausführung wie die Ausführung des übergeordneten Pakets.  
  
 Wenn eine Ausführungs-ID nicht angegeben wird, werden Leistungsstatistiken für mehrere Ausführungen zurückgegeben. Wenn Sie ein Mitglied der **ssis_admin** -Datenbankrolle sind, werden Leistungsstatistiken für alle aktiven Ausführungen zurückgegeben.  Wenn Sie kein Mitglied der **ssis_admin** -Datenbankrolle sind, werden Leistungsstatistiken zu den aktiven Ausführungen zurückgegeben, für die Sie Leseberechtigungen haben. *execution_id* ist **BigInt**.  
  
## <a name="remarks"></a>Remarks  
 In der folgenden Tabelle werden die von der dm_execution_performance_counter-Funktion zurückgegebenen Leistungsindikatornamenswerte aufgeführt.  
  
|Indikatorname|und Beschreibung|  
|------------------|-----------------|  
|Gelesene BLOB-Bytes|Anzahl der Bytes der BLOB-Daten (Binary Large Object), die die Datenfluss-Engine in allen Datenquellen liest.|  
|Geschriebene BLOB-Bytes|Anzahl der Bytes der BLOB-Daten (Binary Large Object), die die Datenfluss-Engine in alle Ziele schreibt.|  
|Verwendete BLOB-Dateien|Anzahl von BLOB-Dateien, die die Datenfluss-Engine zum Spoolen verwendet.|  
|Pufferspeicher|Arbeitsspeicher, der von den Integration Services-Puffern verwendet wird, einschließlich des physischen und virtuellen Arbeitsspeichers.|  
|Verwendete Puffer|Anzahl von Pufferobjekten aller Typen, die alle Datenflusskomponenten und die Datenfluss-Engine verwenden.|  
|Gespoolte Puffer|Anzahl der auf den Datenträger geschriebenen Puffer.|  
|Flatpufferspeicher|Arbeitsspeicher in Bytes, der von allen Flatpuffern verwendet wird. Als Flatpuffer werden Speicherblöcke bezeichnet, die von einer Komponente zum Speichern von Daten verwendet werden.|  
|Verwendete Flatpuffer|Anzahl der von der Datenfluss-Engine verwendeten Flatpuffer. Alle Flatpuffer sind private Puffer.|  
|Privater Pufferspeicher|Arbeitsspeicher, die von allen privaten Puffern verwendet wird. Ein Puffer wird als privat bezeichnet, wenn er von einer Transformation für temporäre Arbeitsvorgänge verwendet wird.<br /><br /> Ein Puffer ist nicht privat, wenn die Datenfluss-Engine den Puffer zur Unterstützung des Datenflusses erstellt.|  
|Private verwendete Puffer|Anzahl von Puffern, die die Transformationen für temporäre Arbeitsvorgänge verwenden.|  
|Gelesene Zeilen|Gesamtzahl der für die Ausführung bereiten Zeilen.|  
|Geschriebene Zeilen|Gesamtzahl der von der Ausführung geschriebenen Zeilen.|  
  
## <a name="return"></a>Rückgabewert  
 Die dm_execution_performance_counters-Funktion gibt für eine aktive Ausführung eine Tabelle mit den folgenden Spalten zurück. Die zurückgegebenen Informationen sind für alle in der Ausführung enthaltenen Pakete. Sind keine Ausführungen aktiv, wird eine leere Tabelle zurückgegeben.  
  
|Spaltenname|Spaltentyp|und Beschreibung|Remarks|  
|-----------------|-----------------|-----------------|-------------|  
|execution_id|**BigInt**<br /><br /> **NULL** ist kein gültiger Wert.|Eindeutiger Bezeichner für die das Paket enthaltende Ausführung.||  
|counter_name|**nvarchar(128)**|Der Name des Leistungsindikators.|Siehe den Abschnitt von Werten **Hinweise** .|  
|counter_value|**BigInt**|Wert, der vom Indikator zurückgegeben wird.||  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel gibt die Funktion Statistiken für eine aktive Ausführung mit einer ID von 34 zurück.  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel gibt die Funktion abhängig von den Berechtigungen Statistiken für alle Ausführungen zurück, die auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server ausgeführt werden.  
  
```sql
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Funktion erfordert eine der folgenden Berechtigungen:  
  
-   READ- und MODIFY-Berechtigungen für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 Die folgende Liste beschreibt Bedingungen, unter denen die Funktion fehlschlägt.  
  
-   Der Benutzer verfügt nicht über MODIFY-Berechtigungen für die angegebene Ausführung.  
  
-   Die angegebene Ausführungs-ID ist ungültig.  
  
  

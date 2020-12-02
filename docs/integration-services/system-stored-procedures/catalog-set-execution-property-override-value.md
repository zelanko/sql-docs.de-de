---
description: catalog.set_execution_property_override_value
title: catalog.set_execution_property_override_value | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1d68015c56a6b5552ebee72f661c879c26aef4a1
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129634"
---
# <a name="catalogset_execution_property_override_value"></a>catalog.set_execution_property_override_value 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt den Wert einer Eigenschaft für eine Instanz der Ausführung im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog fest.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>Argumente  
 [ @execution_id = ] *execution_id*  
 Der eindeutige Bezeichner für die Instanz der Ausführung. Der *execution_id* ist **bigint**.  
  
 [ @property_path = ] *property_path*  
 Der Pfad zur Eigenschaft im Paket. Der *property_path* ist **nvarchar(4000)**.  
  
 [ @property_value = ] *property_value*  
 Der Überschreibungswert, der der Eigenschaft zugewiesen werden soll. Der *property_value* ist **nvarchar(max)** .  
  
 [ @sensitive = ] *sensitive*  
 Wenn der Wert 1 lautet, ist die Eigenschaft vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert 0, ist die Eigenschaft nicht vertraulich, und der Wert wird als Nur-Text gespeichert. Das *sensitive* -Argument lautet **bit**.  
  
## <a name="remarks"></a>Hinweise  
 Diese Prozedur führt die gleiche Funktion wie der Abschnitt **Eigenschaftenüberschreibungen** auf der Registerkarte **Erweitert** des Dialogfelds **Paket ausführen** aus. Der Pfad zur Eigenschaft wird von der Eigenschaft **Paketpfad** des Pakettasks abgeleitet.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
-   Der Ausführungsbezeichner ist ungültig.  
  
-   Der Eigenschaftspfad ist ungültig.  
  
-   Der Datentyp des Eigenschaftswerts stimmt nicht mit dem Datentyp der Eigenschaft überein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  

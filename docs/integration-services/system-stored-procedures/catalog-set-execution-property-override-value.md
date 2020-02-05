---
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
ms.openlocfilehash: a8e85c35552a8bcbf4190bd3ce36b4a65be96789
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71295304"
---
# <a name="catalogset_execution_property_override_value"></a>catalog.set_execution_property_override_value 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
 Der Pfad zur Eigenschaft im Paket. Der *property_path* ist **nvarchar(4000)** .  
  
 [ @property_value = ] *property_value*  
 Der Überschreibungswert, der der Eigenschaft zugewiesen werden soll. Der *property_value* ist **nvarchar(max)** .  
  
 [ @sensitive = ] *sensitive*  
 Wenn der Wert 1 lautet, ist die Eigenschaft vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert 0, ist die Eigenschaft nicht vertraulich, und der Wert wird als Nur-Text gespeichert. Das *sensitive* -Argument lautet **bit**.  
  
## <a name="remarks"></a>Bemerkungen  
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
  
  

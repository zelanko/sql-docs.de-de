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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5f9f4b912a8d57a2c6f2b11f710e414edfadfb94
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58277559"
---
# <a name="catalogsetexecutionpropertyoverridevalue"></a>catalog.set_execution_property_override_value
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
 Der Pfad zur Eigenschaft im Paket. Der *property_path* ist **nvarchar(4000)**.  
  
 [ @property_value = ] *property_value*  
 Der Überschreibungswert, der der Eigenschaft zugewiesen werden soll. Der *property_value* ist **nvarchar(max)**.  
  
 [ @sensitive = ] *sensitive*  
 Wenn der Wert 1 lautet, ist die Eigenschaft vertraulich und wird beim Speichern verschlüsselt. Lautet der Wert 0, ist die Eigenschaft nicht vertraulich, und der Wert wird als Nur-Text gespeichert. Das *sensitive* -Argument lautet **bit**.  
  
## <a name="remarks"></a>Remarks  
 Diese Prozedur führt die gleiche Funktion wie der Abschnitt **Eigenschaftenüberschreibungen** auf der Registerkarte **Erweitert** des Dialogfelds **Paket ausführen** aus. Der Pfad zur Eigenschaft wird von der Eigenschaft **Paketpfad** des Pakettasks abgeleitet.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
-   Der Ausführungsbezeichner ist ungültig.  
  
-   Der Eigenschaftspfad ist ungültig.  
  
-   Der Datentyp des Eigenschaftswerts stimmt nicht mit dem Datentyp der Eigenschaft überein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  

---
title: catalog.execution_parameter_values (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: ec93e67b-04ce-4aae-ab96-3ad20e9793ad
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a018123080076cfcc3886395345e29df62feed79
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65714741"
---
# <a name="catalogexecutionparametervalues-ssisdb-database"></a>catalog.execution_parameter_values (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die tatsächlichen Parameterwerte an, die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen während einer Instanz der Ausführung verwendet werden.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|execution_parameter_id|**bigint**|Eindeutiger Bezeichner (ID) des Ausführungsparameters.|  
|execution_id|**bigint**|Eindeutige ID für die Instanz der Ausführung.|  
|object_type|**smallint**|Wenn der Wert `20`ist, ist der Parameter ein Projektparameter. Wenn der Wert `30`ist, ist der Parameter ein Paketparameter. Wenn der Wert `50` ist, entspricht der Parameter einem der folgenden Werte:<br /><br /> **LOGGING_LEVEL**<br /><br /> **DUMP_ON_ERROR**<br /><br /> **DUMP_ON_EVENT**<br /><br /> **DUMP_EVENT_CODE**<br /><br /> **CALLER_INFO**<br /><br /> **SYNCHRONIZED**|  
|parameter_data_type|**nvarchar(128)**|Der Datentyp des Parameters.|  
|parameter_name|**sysname**|Der Name des Parameters.|  
|parameter_value|**sql_variant**|Der Wert des Parameters. Wenn `0` vertraulich ist, wird der Nur-Text-Wert angezeigt. Wenn `1` vertraulich ist, wird der Wert **NULL** angezeigt.|  
|sensitive|**bit**|Wenn der Wert `1`lautet, ist der Parameterwert vertraulich. Wenn der Wert `0`lautet, ist der Parameterwert nicht vertraulich.|  
|erforderlich|**bit**|Wenn der Wert `1`lautet, ist der Parameterwert erforderlich, um die Ausführung zu starten. Wenn der Wert `0`lautet, ist der Parameterwert nicht erforderlich, um die Ausführung zu starten.|  
|value_set|**bit**|Wenn der Wert `1`ist, wurde der Parameterwert zugewiesen. Wenn der Wert `0`ist, wurde der Parameterwert nicht zugewiesen.|  
|runtime_override|**bit**|Wenn der Wert `1`ist, wurde der ursprüngliche Parameterwert geändert, bevor die Ausführung gestartet wurde. Wenn der Wert `0`lautet, ist der Parameterwert der ursprünglich festgelegte Wert.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht wird eine Zeile für jeden Ausführungsparameter im Katalog angezeigt. Ein Ausführungsparameterwert ist der Wert, der einem Projektparameter oder Paketparameter während einer einzelnen Instanz der Ausführung zugewiesen wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  

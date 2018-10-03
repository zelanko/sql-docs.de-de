---
title: catalog.executables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: bae22d0c-e190-426f-a074-c1d1170e8dd8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cca22286db2bb959a3aecb6524528292a207eedc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817518"
---
# <a name="catalogexecutables"></a>catalog.executables
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In dieser Sicht wird eine Zeile für jede ausführbare Datei in der angegebenen Ausführung angezeigt.  
  
 Eine ausführbare Datei ist ein Task oder ein Container, den Sie der Ablaufsteuerung eines Pakets hinzufügen.  
  
|Spaltenname|**Data type**|und Beschreibung|  
|-----------------|-------------------|-----------------|  
|executable_id|**bigint**|Der eindeutige Bezeichner für die ausführbare Datei.|  
|execution_id|**bigint**|Der eindeutige Bezeichner für die Instanz der Ausführung.|  
|executable_name|**nvarchar(4000)**|Der Name der ausführbaren Datei.|  
|executable_guid|**nvarchar(38)**|Die GUID der ausführbaren Datei.|  
|package_name|**nvarchar(260)**|Der Name des Pakets.|  
|package_path|**nvarchar(max)**|Der Pfad des Pakets.|  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
## <a name="remarks"></a>Remarks  
  

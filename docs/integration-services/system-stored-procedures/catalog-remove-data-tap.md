---
title: catalog.remove_data_tap | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc76e5f5d710dfe088a27376af4f3938257a0ec7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296828"
---
# <a name="catalogremove_data_tap"></a>catalog.remove_data_tap 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Entfernt eine Datenabzweigung aus einer Komponentenausgabe, die aktuell ausgeführt wird. Der eindeutige Bezeichner für die Datenabzweigung ist einer Instanz der Ausführung zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Argumente  
 [ @data_tap_id = ] *data_tap_id*  
 Der eindeutige Bezeichner für die Datenabzweigung, die mit der gespeicherten Prozedur "catalog.add_data_tap" erstellt wird. Der *data_tap_id* ist **bigint**.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Paket mehrere Datenflusstasks mit dem gleichen Namen enthält, wird die Datenabzweigung dem ersten Datenflusstask mit dem angegebenen Namen hinzugefügt.  
  
## <a name="return-codes"></a>Rückgabecodes  
 0 (Erfolg)  
  
 Wenn die gespeicherte Prozedur fehlschlägt, wird ein Fehler ausgelöst.  
  
## <a name="result-set"></a>Resultset  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Um Datenabzweigungen zu entfernen, muss die Ausführungsinstanz den Status „Erstellt“ (einen Wert von 1 in der Spalte **Zustand** der Sicht [catalog.operations &#40;SSISDB-Datenbank&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)) aufweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   MODIFY-Berechtigungen für die Instanz der Ausführung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 Die folgende Liste beschreibt Bedingungen, unter denen die gespeicherte Prozedur fehlschlägt.  
  
-   Der Benutzer verfügt nicht über MODIFY-Berechtigungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  

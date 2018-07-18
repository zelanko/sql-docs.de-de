---
title: Neue Benutzerrolle (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
caps.latest.revision: 25
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6654b0bef25504737e2f3fb42cdb2b0f8d017506
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251362"
---
# <a name="new-user-role-management-studio"></a>Neue Benutzerrolle (Management Studio)
  Verwenden Sie diese Seite, um eine Rollendefinition auf Elementebene zu erstellen. Eine Rollendefinition auf Elementebene ist eine benannte Auflistung von Tasks, die Benutzer in Bezug auf Ordner, Berichte, Modelle, Ressourcen und freigegebene Datenquellen ausführen können. Ein Beispiel für eine Rollendefinition auf Elementebene ist die vordefinierte Rolle Browser, die Aktionen identifiziert, die der Endbenutzer eines Berichts zum Navigieren in Ordnern und zum Anzeigen von Berichten verwenden kann.  
  
 Es sollten nur wenige Rollendefinitionen verwendet werden. In den meisten Anwendungen sind wenige Rollendefinitionen auch ausreichend. Wenn die vordefinierten Rollendefinitionen jedoch nicht ausreichend sind, können Sie diese bearbeiten oder neue erstellen.  
  
> [!NOTE]  
>  Rollendefinitionen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Rollendefinition ein. Ein Rollendefinitionsname muss innerhalb des Berichtsserver-Namespaces eindeutig sein. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : @ & = +, $ / * \< >  
  
 " /  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung ein, in der die Verwendung der Rolle erläutert wird, und die Art der Unterstützung durch die Rolle aufgeführt ist.  
  
 **Task**  
 Wählen Sie die Tasks aus, die über diese Rolle ausgeführt werden können. Sie können keine neuen, von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützten Tasks erstellen oder solche vorhandenen Tasks ändern. In einer Rollendefinition auf Elementebene können nur Tasks auf Elementebene verwendet werden.  
  
 **Taskbeschreibung**  
 Zeigt eine Beschreibung des Tasks an, in der die durch den Task unterstützten Vorgänge bzw. Berechtigungen aufgeführt sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Rollendefinitionen](../security/role-definitions.md)  
  
  

---
title: Neue Benutzerrolle (Management Studio) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.newrole.f1
ms.assetid: 9f76a235-0b58-479c-8e5b-50588091b71c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 16f083c08a9d82a019ae98a8f9a71d7e596394da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65582180"
---
# <a name="new-user-role-management-studio"></a>Neue Benutzerrolle (Management Studio)
  Verwenden Sie diese Seite, um eine Rollendefinition auf Elementebene zu erstellen. Eine Rollendefinition auf Elementebene ist eine benannte Auflistung von Tasks, die Benutzer in Bezug auf Ordner, Berichte, Modelle, Ressourcen und freigegebene Datenquellen ausführen können. Ein Beispiel für eine Rollendefinition auf Elementebene ist die vordefinierte Rolle Browser, die Aktionen identifiziert, die der Endbenutzer eines Berichts zum Navigieren in Ordnern und zum Anzeigen von Berichten verwenden kann.  
  
 Es sollten nur wenige Rollendefinitionen verwendet werden. In den meisten Anwendungen sind wenige Rollendefinitionen auch ausreichend. Wenn die vordefinierten Rollendefinitionen jedoch nicht ausreichend sind, können Sie diese bearbeiten oder neue erstellen.  
  
> [!NOTE]  
>  Rollendefinitionen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>enthalten  
 **Name**  
 Geben Sie den Namen der Rollendefinition ein. Ein Rollendefinitionsname muss innerhalb des Berichtsserver-Namespaces eindeutig sein. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = + , $ / * < >  
  
 " /  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung ein, in der die Verwendung der Rolle erläutert wird, und die Art der Unterstützung durch die Rolle aufgeführt ist.  
  
 **Task**  
 Wählen Sie die Tasks aus, die über diese Rolle ausgeführt werden können. Sie können keine neuen, von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützten Tasks erstellen oder solche vorhandenen Tasks ändern. In einer Rollendefinition auf Elementebene können nur Tasks auf Elementebene verwendet werden.  
  
 **Taskbeschreibung**  
 Zeigt eine Beschreibung des Tasks an, in der die durch den Task unterstützten Vorgänge bzw. Berechtigungen aufgeführt sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserver im Management Studio (F1-Hilfe)](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Rollendefinitionen](../../reporting-services/security/role-definitions.md)  
  
  

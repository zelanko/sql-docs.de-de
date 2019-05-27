---
title: Neue Systemrolle (Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d9227136ba3bd1526f8ec04476d6dc5d61ca41f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66100182"
---
# <a name="new-system-role-management-studio"></a>Neue Systemrolle (Management Studio)
  Verwenden Sie diese Seite, um eine Rollendefinition auf Systemebene zu erstellen. Eine Systemrollendefinition gibt eine Gruppe von Aufgaben auf Systemebene an, die für den gesamten Berichtsserver gültig sind.  
  
> [!NOTE]  
>  Rollendefinitionen werden nur auf einem Berichtsserver verwendet, der im einheitlichen Modus ausgeführt wird. Ist der Berichtsserver für den integrierten SharePoint-Modus konfiguriert, ist diese Seite nicht verfügbar.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie den Namen der Rollendefinition ein. Ein Rollendefinitionsname muss innerhalb des Berichtsserver-Namespaces eindeutig sein. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und Sonderzeichen enthalten. Folgende Zeichen können beim Angeben eines Namens nicht verwendet werden:  
  
 ; ? : \@ & = + , $ / * \< >  
  
 " /  
  
 **Beschreibung**  
 Stellen Sie eine Beschreibung bereit, in der die Verwendung der Rolle erläutert wird, und die Art der Unterstützung durch die Rolle aufgeführt ist.  
  
 **Task**  
 Wählen Sie die Tasks auf Systemebene aus, die über diese Rolle ausgeführt werden können. Sie können keine neuen, von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]unterstützten Tasks erstellen oder solche vorhandenen Tasks ändern. Außerdem können Sie keine Tasks auf Elementebene für eine Systemrollendefinition auswählen.  
  
 **Taskbeschreibung**  
 Zeigt eine Beschreibung des Tasks an, in der die durch den Task unterstützten Vorgänge bzw. Berechtigungen aufgeführt sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Rollendefinitionen](../security/role-definitions.md)  
  
  

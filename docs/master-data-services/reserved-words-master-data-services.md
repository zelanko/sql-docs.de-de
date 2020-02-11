---
title: Reservierte Wörter
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 817e15d2fe7e91f63628826f58d6a86dd4edbcb3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727918"
---
# <a name="reserved-words-master-data-services"></a>Reservierte Wörter (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Wenn Sie Modellobjekte oder Elemente erstellen, können in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einige Wörter nicht verwendet werden. Die Verwendung dieser Wörter verursacht möglicherweise Fehler.  
  
> [!NOTE]  
>  Sie sollten auch die Verwendung von Sonderzeichen (Symbole, Silbentrennung usw.) einschränken.  
  
-   [Modelle](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Entitäten](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Explizite Hierarchien](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Attribute](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Mitglieder](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a>Bilder  
 Wenn Sie ein Modell erstellen, dessen Name auf **Name** oder **Code**festgelegt ist, darf **Entität mit demselben Namen wie das Modell erstellen** nicht ausgewählt werden, weil **Name** oder **Code** nicht für den Namen einer Entität verwendet werden kann.  
  
##  <a name="entities"></a>Kleinstunternehmen  
 
  **Name** oder **Code**kann für Entitätsnamen nicht verwendet werden.  
  
##  <a name="exhierarchies"></a>Explizite Hierarchien  
 Für explizite Hierarchienamen können Sie **Name** oder **Code**verwenden.  
  
##  <a name="attributes"></a>Legt  
  
-   **id**  
  
-   **Code**  
  
-   **Enter username**  
  
-   **Lastchgusername**  
  
-   **Name**  
  
-   **Enterdtm**  
  
-   **Enteruserid**  
  
-   **Enter username**  
  
-   **Lastchgdtm**  
  
-   **Lastchguserid**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a>Parlamentariern  
 Bei Elementen kann **MDMMemberStatus**, **MDMUnused**oder **ROOT** nicht für den Attributwert **Code** verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Master Data Services Übersicht &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
  

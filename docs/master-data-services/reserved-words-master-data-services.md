---
title: Reservierte Wörter (Master Data Services) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: f12b95a192535b037f01a601146a0bba544d8fae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65485961"
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
  
-   [Element](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> Modelle  
 Wenn Sie ein Modell erstellen, dessen Name auf **Name** oder **Code**festgelegt ist, darf **Entität mit demselben Namen wie das Modell erstellen** nicht ausgewählt werden, weil **Name** oder **Code** nicht für den Namen einer Entität verwendet werden kann.  
  
##  <a name="entities"></a> Entitäten  
 **Name** oder **Code**kann für Entitätsnamen nicht verwendet werden.  
  
##  <a name="exhierarchies"></a> Explizite Hierarchien  
 Für explizite Hierarchienamen können Sie **Name** oder **Code**verwenden.  
  
##  <a name="attributes"></a> Attribute  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Name**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> Element  
 Bei Elementen kann **MDMMemberStatus**, **MDMUnused**oder **ROOT** nicht für den Attributwert **Code** verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
  

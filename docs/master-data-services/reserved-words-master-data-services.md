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
ms.openlocfilehash: 78dcf9320312f93dd08495f21bf0f6cc1b71516b
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811458"
---
# <a name="reserved-words-master-data-services"></a>Reservierte Wörter (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Wenn Sie Modellobjekte oder Elemente erstellen, können in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einige Wörter nicht verwendet werden. Die Verwendung dieser Wörter verursacht möglicherweise Fehler.  
  
> [!NOTE]  
>  Sie sollten auch die Verwendung von Sonderzeichen (Symbole, Silbentrennung usw.) einschränken.  
  
-   [Modelle](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [Entitäten](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [Explizite Hierarchien](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [Attribute](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [Mitglieder](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a><a name="models"></a>Bilder  
 Wenn Sie ein Modell erstellen, dessen Name auf **Name** oder **Code**festgelegt ist, darf **Entität mit demselben Namen wie das Modell erstellen** nicht ausgewählt werden, weil **Name** oder **Code** nicht für den Namen einer Entität verwendet werden kann.  
  
##  <a name="entities"></a><a name="entities"></a>Kleinstunternehmen  
 **Name** oder **Code**kann für Entitätsnamen nicht verwendet werden.  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a>Explizite Hierarchien  
 Für explizite Hierarchienamen können Sie **Name** oder **Code**verwenden.  
  
##  <a name="attributes"></a><a name="attributes"></a>Legt  
  
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
  
##  <a name="members"></a><a name="members"></a>Parlamentariern  
 Bei Elementen kann **MDMMemberStatus**, **MDMUnused**oder **ROOT** nicht für den Attributwert **Code** verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
  

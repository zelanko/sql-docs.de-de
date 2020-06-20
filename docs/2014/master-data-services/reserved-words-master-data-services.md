---
title: Reservierte Wörter (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cd1e5bcee01992607cf9bffca1a72dd99bd75fbe
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960580"
---
# <a name="reserved-words-master-data-services"></a>Reservierte Wörter (Master Data Services)
  Wenn Sie Modellobjekte oder Elemente erstellen, können in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einige Wörter nicht verwendet werden. Die Verwendung dieser Wörter verursacht möglicherweise Fehler.  
  
> [!NOTE]  
>  Sie sollten auch die Verwendung von Sonderzeichen (Symbole, Silbentrennung usw.) einschränken.  
  
-   [Modelle](#models)  
  
-   [Entitäten](#entities)  
  
-   [Explizite Hierarchien](#exhierarchies)  
  
-   [Attribute](#attributes)  
  
-   [Mitglieder](#members)  
  
##  <a name="models"></a><a name="models"></a>Bilder  
 Wenn Sie ein Modell erstellen, dessen Name auf **Name**festgelegt ist, wählen Sie **Entität mit gleichem Namen wie Modell erstellen** nicht aus, da **Name** nicht für den Namen einer Entität verwendet werden kann.  
  
##  <a name="entities"></a><a name="entities"></a>Kleinstunternehmen  
 **Name** oder **Code**kann für Entitätsnamen nicht verwendet werden.  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a>Explizite Hierarchien  
 Für explizite Hierarchienamen können Sie **Name** oder **Code**verwenden.  
  
##  <a name="attributes"></a><a name="attributes"></a>Legt  
  
-   **ID**  
  
-   **Code**  
  
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
 Für Member können Sie **mdmmembership Status** oder **root** nicht für den **Code** Attribut Wert verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über Master Data Services](master-data-services-overview-mds.md)  
  
  

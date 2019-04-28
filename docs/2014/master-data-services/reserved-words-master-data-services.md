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
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 49d4a633e7d03dc03e3eba95067e448cbb323e0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923216"
---
# <a name="reserved-words-master-data-services"></a>Reservierte Wörter (Master Data Services)
  Wenn Sie Modellobjekte oder Elemente erstellen, können in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einige Wörter nicht verwendet werden. Die Verwendung dieser Wörter verursacht möglicherweise Fehler.  
  
> [!NOTE]  
>  Sie sollten auch die Verwendung von Sonderzeichen (Symbole, Silbentrennung usw.) einschränken.  
  
-   [Modelle](#models)  
  
-   [Entitäten](#entities)  
  
-   [Explizite Hierarchien](#exhierarchies)  
  
-   [Attribute](#attributes)  
  
-   [Element](#members)  
  
##  <a name="models"></a> Modelle  
 Bei der Erstellung eines Modells mit dem Namen festgelegt **Namen**, aktivieren Sie nicht **Entität mit demselben Namen wie Modell erstellen** da **Namen** kann nicht für den Namen einer Entität verwendet werden.  
  
##  <a name="entities"></a> Entitäten  
 **Name** oder **Code**kann für Entitätsnamen nicht verwendet werden.  
  
##  <a name="exhierarchies"></a> Explizite Hierarchien  
 Für explizite Hierarchienamen können Sie **Name** oder **Code**verwenden.  
  
##  <a name="attributes"></a> Attribute  
  
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
  
##  <a name="members"></a> Element  
 Für Elemente können keine **MDMMemberStatus** oder **Stamm** für die **Code** Attributwert.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Master Data Services](master-data-services-overview-mds.md)  
  
  

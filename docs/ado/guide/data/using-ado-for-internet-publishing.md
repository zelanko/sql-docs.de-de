---
title: Verwenden von ADO für die Internet Veröffentlichung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: decbc7c3b377234d91fe6b3e662d9449298041c1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923617"
---
# <a name="using-ado-for-internet-publishing"></a>Verwenden von ADO für die Veröffentlichung im Internet
[Der OLE DB Anbieter für die Internet Veröffentlichung](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) zeigt ein bestimmtes Beispiel für den Zugriff auf heterogene Daten mit ADO. Obwohl die Beispiele in diesem Abschnitt speziell für die Verwendung des Internet Publishing Anbieters gelten, sollten die gezeigten Prinzipien ähnlich sein, wenn Sie ADO mit anderen Anbietern für heterogene Daten verwenden, z. b. ein Anbieter in einem e-Mail-Speicher.  
  
## <a name="urls"></a>URLs  
 URL (Uniform Resource Locators) können als Alternative zu Verbindungs Zeichenfolgen und Befehls Text verwendet werden, um Datenquellen und den Speicherort von Dateien und Verzeichnissen anzugeben. Sie können URLs mit den vorhandenen [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) -und **Recordset** -Objekten sowie mit den **Datensatz** -und **Stream** -Objekten verwenden.  
  
 Weitere Informationen zur Verwendung von URLs finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Daten Satz Felder  
 Der Unterschied zwischen heterogenen Daten und homogenen Daten besteht darin, dass für die erste, jede Daten Zeile oder jeden **Datensatz**eine andere Gruppe von Spalten oder **Feldern**vorhanden sein kann. Bei homogenen Daten hat jede Zeile denselben Satz von Spalten. Weitere Informationen zu den Feldern, die für den Internet Publishing Provider spezifisch sind, finden Sie unter [Datensätze und vom Anbieter bereitgestellte zusätzliche Felder](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Anhängen neuer Felder  
 Mehrere ADO-Objekte wurden verbessert, um zusammen mit **Datensatz** -und **Streamobjekten** zusammenzuarbeiten.  
  
-   Die [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung, mit der der Auflistung ein [Feld](../../../ado/reference/ado-api/field-object.md) Objekt erstellt und hinzugefügt wird, kann auch den Wert des **Felds**angeben.  
  
-   Die [Update](../../../ado/reference/ado-api/update-method.md) -Methode schließt das Hinzufügen oder Löschen von Feldern zur Auflistung ab.  
  
-   Als Verknüpfung und Alternative zur **Append** -Methode können Sie Felder erstellen, indem Sie einem nicht definierten oder zuvor gelöschten Feld einen Wert zuweisen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Der OLE DB-Anbieter für die Veröffentlichung im Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Internet Publishing Scenario (Internet-Publishing-Szenario)](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [Absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Datensätze und von Anbietern bereitgestellte Felder](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [ADO-Verlauf](../../../ado/guide/ado-history.md)

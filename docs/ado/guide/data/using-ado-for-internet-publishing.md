---
title: Verwenden von ADO für Internet Publishing | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: ac7922dda2d486f4783d1230296dc89b81cb4fe3
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718608"
---
# <a name="using-ado-for-internet-publishing"></a>Verwenden von ADO für die Veröffentlichung im Internet
[Der OLE DB-Anbieter für Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) zeigt ein Beispiel für den Zugriff auf heterogene Daten mit ADO. Obwohl in die Beispielen in diesem Abschnitt werden über die Verwendung der Internet-Publishing-Anbieter ist, sollte der dargestellten Prinzipien ähneln bei Verwendung von ADO mit anderen Anbietern für heterogene Daten, z. B. ein Provider in einen Speicher-e-Mail.  
  
## <a name="urls"></a>URLs  
 Uniform Resource Locator (URLs) können als Alternative zu Verbindungszeichenfolgen und Befehlstext an Datenquellen und den Speicherort der Dateien und Verzeichnissen verwendet werden. Sie können URLs verwenden, mit dem vorhandenen [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) und **Recordset** Objekte und mit der **Datensatz** und **Stream** Objekte.  
  
 Weitere Informationen zur Verwendung von URLs finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>Notieren Sie die Felder  
 Der entscheidende Unterschied zwischen heterogenen Daten und homogene Daten ist, die für die ehemalige, jede Zeile der Daten oder **Datensatz**, haben Sie einen anderen Satz von Spalten oder **Felder**. Für homogene Daten weist jede Zeile den gleichen Satz von Spalten. Weitere Informationen zu den Feldern, die spezifisch für den Internet-Publishing-Anbieter finden Sie unter [Datensätze und vom Anbieter bereitgestellte zusätzliche Felder](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Anfügen von neuen Felder  
 Mehrere ADO-Objekte wurden verbessert, damit arbeiten zusammen mit **Datensatz** und **Stream** Objekte.  
  
-   Die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung [Append](../../../ado/reference/ado-api/append-method-ado.md) -Methode, die erstellt und fügt eine [Feld](../../../ado/reference/ado-api/field-object.md) Objekt der Auflistung, die den Wert des können auch angeben der **Feld**.  
  
-   Die [Update](../../../ado/reference/ado-api/update-method.md) Methode schließt ab, das Hinzufügen oder Löschen von Feldern in der Auflistung.  
  
-   Als Alternative zur Verknüpfung und der **Anfügen** -Methode, Sie können Felder durch Zuweisen eines Werts in ein Feld nicht definiert oder zuvor gelöschten erstellen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Der OLE DB-Anbieter für Internet-Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Internet Publishing Scenario (Internet-Publishing-Szenario)](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [Absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Records and Provider-Supplied Fields (Datensätze und von Anbietern bereitgestellte Felder)](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Record Object (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [ADO-Verlauf](../../../ado/guide/ado-history.md)

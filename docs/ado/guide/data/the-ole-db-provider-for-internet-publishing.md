---
title: OLE DB-Anbieter für Internet Publishing | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f70970ec872d3c921fa10e3eacb1c54d7c4de2d4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632208"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Der OLE DB-Anbieter für die Veröffentlichung im Internet
Das ADO [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) und [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekte können verwendet werden mit der Microsoft OLE DB-Anbieter für Internet Publishing (Internet-Publishing-Anbieter) aufrufen und Bearbeiten von Ressourcen, z. B. Web-Ordner oder Dateien von Microsoft FrontPage bedient. Bei ADO können Sie geben die Quelle für eine **Datensatz**, **Stream**, oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) eine URL sein. Sie können dann hochladen, herunterladen, verschieben, kopieren und Löschen von Ressourcen oder Ressourceneigenschaften direkt bearbeiten.  
  
 Z. B. Code, der verwendet **Datensätze** und **Streams** mit dem Internet-Publishing-Anbieter finden Sie unter den [Internet-Publishing-Szenario](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Die Internet-Publishing-Anbieter wird mit Microsoft Windows 2000 installiert. Frühere Versionen von Internet-Publishing-Anbieter sind auch verfügbar, mit Microsoft Office 2000 und Microsoft Internet Explorer 5.0.  
  
 Es gibt drei Möglichkeiten, ADO mit dem Internet-Publishing-Anbieter hergestellt:  
  
-   Geben Sie "URL =" in der Verbindungszeichenfolge. Zum Beispiel:  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   Geben Sie Msdaipp.dso für die *Anbieter* -Schlüsselwort der Verbindungszeichenfolge. Zum Beispiel:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   Geben Sie Msdaipp.dso für die [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Zum Beispiel:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Wenn Msdaipp.dso explizit angegeben wird, als Wert für den Anbieter, entweder mit der *Anbieter* -Schlüsselwort der Verbindungszeichenfolge oder die **Anbieter** -Eigenschaft, können keine "URL =" in der Verbindungszeichenfolge. Wenn Sie dies tun, tritt ein Fehler auf. Geben Sie stattdessen einfach die URL wie oben beschrieben.  
  
 Genauere Informationen zu den Internet-Publishing-Anbieter, finden Sie unter [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), oder in der Dokumentation bereitgestellt, mit der Source-Anwendung mit dem der OLE DB-Anbieter für Internet Publishing installiert wurde: Windows 2000, Office 2000 oder Internet Explorer 5.0.

---
title: Der OLE DB Anbieter für die Internet Veröffentlichung | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 813b7e108f375fdbd22ba10761678907aea912f6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759056"
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Der OLE DB-Anbieter für die Veröffentlichung im Internet
Die ADO- [Daten Satz](../../../ado/reference/ado-api/record-object-ado.md) -und [Streamobjekte](../../../ado/reference/ado-api/stream-object-ado.md) können mit dem Microsoft OLE DB-Anbieter für die Internetveröffentlichung (Internet Publishing Provider) verwendet werden, um auf Ressourcen zuzugreifen und Sie zu bearbeiten, wie z. b. Webordner oder von Microsoft FrontPage bereitgestellte Dateien Mit ADO können Sie die Quelle eines **Datensatzes**, **Streams**oder [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) als URL angeben. Anschließend können Sie Ressourcen hochladen, herunterladen, verschieben, kopieren und löschen oder Ressourcen Eigenschaften direkt bearbeiten.  
  
 Beispielcode, der **Datensätze** und **Streams** mit dem Internet Publishing Provider verwendet, finden Sie im [Internet Publishing-Szenario](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Der Internet Publishing Provider wird mit Microsoft Windows 2000 installiert. Frühere Versionen des Internet Publishing Anbieters sind auch mit Microsoft Office 2000 und Microsoft Internet Explorer 5,0 verfügbar.  
  
 Es gibt drei Möglichkeiten, ADO mit dem Internet Publishing Provider zu verbinden:  
  
-   Geben Sie "URL =" in der Verbindungs Zeichenfolge an. Beispiel:  
  
    ```  
    objConn.Open "URL=https://servername"  
    ```  
  
-   Geben Sie msdaipp. DSO für das *Provider* -Schlüsselwort der Verbindungs Zeichenfolge an. Beispiel:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=https://servername"  
    ```  
  
-   Geben Sie msdaipp. DSO für die [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft des [Connection](../../../ado/reference/ado-api/connection-object-ado.md) -Objekts an. Beispiel:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "https://servername"  
    ```  
  
> [!NOTE]
>  Wenn msdaipp. DSO explizit als Wert des Anbieters angegeben ist, entweder mit dem Schlüsselwort für die Verbindungs Zeichenfolge des *Anbieters* oder mit der **Provider** -Eigenschaft, können Sie "URL =" nicht in der Verbindungs Zeichenfolge verwenden. Wenn Sie dies tun, tritt ein Fehler auf. Geben Sie stattdessen einfach die URL an, wie zuvor gezeigt.  
  
 Spezifischere Informationen zum Internet Publishing Provider finden Sie unter [Microsoft OLE DB-Anbieter für die Internetveröffentlichung](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)oder in der Anbieter Dokumentation, die mit der Quell Anwendung bereitgestellt wird, mit der der OLE DB Anbieter für die Internetveröffentlichung installiert wurde: Windows 2000, Office 2000 oder Internet Explorer 5,0.

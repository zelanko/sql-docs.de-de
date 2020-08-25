---
description: Übersicht über Microsoft OLE DB-Anbieter für Internet Publishing
title: Microsoft OLE DB-Anbieter für die Internet Veröffentlichung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
author: rothja
ms.author: jroth
ms.openlocfilehash: 3888cf881fd1b6cdb0ccc2c5985fe4a6e08ae581
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806587"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Übersicht über Microsoft OLE DB-Anbieter für Internet Publishing
Der Microsoft OLE DB-Anbieter für die Internet Veröffentlichung ermöglicht ADO den Zugriff auf Ressourcen, die von Microsoft FrontPage oder Microsoft Internet Information Server bereitgestellt werden. Zu den Ressourcen gehören webquell Dateien, z. b. HTML-Dateien oder Windows 2000-Webordner.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das *Provider* -Argument der [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf fest, um eine Verbindung mit diesem Anbieter herzustellen:

```vb
MSDAIPP.DSO
```

 Dieser Wert kann auch mit der [Provider](../../reference/ado-api/provider-property-ado.md) -Eigenschaft festgelegt oder gelesen werden.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 - oder -

```vb
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Schlüsselwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für die Internet Veröffentlichung an.|
|**Datenquelle** -oder- **URL**|Gibt die URL einer Datei oder eines Verzeichnisses an, die in einem Webordner veröffentlicht wird.|
|**Benutzer-ID**|Gibt den Benutzernamen an.|
|**Kennwort**|Gibt das Benutzer Kennwort an.|

> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.

 Wenn Sie den *resourceurl* -Wert von "URL =" in der Verbindungs Zeichenfolge auf einen ungültigen Wert festlegen, löst der Internet Publishing Provider standardmäßig ein Dialogfeld aus, in dem Sie zur Eingabe eines gültigen Werts aufgefordert werden. Dies ist ein unerwünschtes Verhalten für eine Komponente in der mittleren Ebene einer Anwendung, da die Programmausführung angehalten wird, bis das Dialogfeld gelöscht wird und der Client so fixiert wird, dass er nicht mehr eine Antwort von der Komponente empfangen hat.

> [!NOTE]
>  Wenn msdaipp. DSO wird explizit als Wert des Anbieters angegeben. entweder mit dem Schlüsselwort für die Verbindungs Zeichenfolge des *Anbieters* oder mit der Eigenschaft " **Provider** " können Sie "URL =" nicht in der Verbindungs Zeichenfolge verwenden. Wenn Sie dies tun, tritt ein Fehler auf. Stattdessen geben Sie einfach die URL an, wie im Thema [Verwenden von ADO mit dem OLE DB Anbieter für die Internet Veröffentlichung](../data/the-ole-db-provider-for-internet-publishing.md)gezeigt.

## <a name="see-also"></a>Weitere Informationen
 [Internet Publishing-Szenario](../data/internet-publishing-scenario.md) [der OLE DB Anbieter für die Internetveröffentlichung](../data/the-ole-db-provider-for-internet-publishing.md)
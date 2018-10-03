---
title: Microsoft OLE DB-Anbieter für Internet Publishing | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56e780efde72007d9ed4f1b701cde220a0f9be4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688118"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Microsoft OLE DB-Anbieter für Internet Publishing (Übersicht)
Microsoft OLE DB-Anbieter für Internet Publishing ermöglicht ADO, um den Zugriff auf Ressourcen von Microsoft FrontPage oder Microsoft Internet Information Server bedient. Ressourcen umfassen Quelle Webdateien z. B. HTML-Dateien oder Ordner von Windows 2000 Web.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die *Anbieter* Argument der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```
MSDAIPP.DSO
```

 Dieser Wert kann auch festlegen oder Lesen Sie mithilfe der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 -oder-

```
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, die OLE DB-Anbieter für Internet Publishing.|
|**Datenquelle** – oder – **URL**|Gibt die URL einer Datei oder Verzeichnis in einen Webordner veröffentlicht.|
|**Benutzer-ID**|Gibt den Benutzernamen an.|
|**Kennwort**|Gibt das Kennwort des Benutzers an.|

> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.

 Setzen Sie die *ResourceURL* Wert aus der "URL =" in der Verbindungszeichenfolge auf einen ungültigen Wert wird standardmäßig ein Dialogfeld mit der Aufforderung einen gültigen Wert der Internet-Publishing-Anbieter löst. Dies ist unerwünschtes Verhalten für eine Komponente in der mittleren Ebene einer Anwendung, da es hält die Ausführung des Programms, bis das Dialogfeld deaktiviert ist, und der Client wird angezeigt, so fixieren, weil keine Antwort von der Komponente empfangen wurde.

> [!NOTE]
>  Wenn MSDAIPP. DSO wird explizit angegeben, als Wert für den Anbieter, entweder mit der *Anbieter* -Schlüsselwort der Verbindungszeichenfolge oder die **Anbieter** -Eigenschaft, können keine "URL =" in der Verbindungszeichenfolge. Wenn Sie dies tun, tritt ein Fehler auf. Geben Sie stattdessen einfach die URL wie im Thema dargestellt [mithilfe von ADO mit dem OLE DB-Anbieter für Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>Siehe auch
 [Internet Publishing-Szenario](../../../ado/guide/data/internet-publishing-scenario.md) [OLE DB-Anbieter für Internet-Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)

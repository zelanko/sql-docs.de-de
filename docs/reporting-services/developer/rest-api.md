---
title: Entwickeln mit REST-APIs für Reporting Services | Microsoft-Dokumentation
ms.description: The REST API provides programmatic access to the objects in a SQL Server 2017 Reporting Services report server catalog.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: developer
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/12/2018
ms.openlocfilehash: d4f4af8dc03713046915f61effc684003303aaa9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502740"
---
# <a name="develop-with-the-rest-apis-for-reporting-services"></a>Entwickeln mit REST-APIs für Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

Microsoft SQL Server 2017 Reporting Services unterstützen Representational State Transfer-APIs (REST). Diese REST-APIs sind Dienstendpunkte, die verschiedene HTTP-Vorgänge (Methoden) unterstützen, die Zugriff auf Ressourcen in einem Berichtsserver herstellen, abrufen, aktualisieren oder löschen.

Die REST-API stellt programmgesteuerten Zugriff auf die Objekte in einem SQL Server 2017 Reporting Services-Berichtsserverkatalog bereit. Bei diesen Objekten handelt es sich beispielsweise um Ordner, Berichte, KPIs, Datenquellen, Datasets, Aktualisierungspläne, Abonnements, etc. Mithilfe der REST-API können Sie z.B. die Ordnerhierarchie navigieren, die Inhalte eines Ordners ermitteln oder eine Berichtsdefinition herunterladen. Außerdem können Sie Objekte erstellen, aktualisieren und löschen. Die Objekte unterstützen Sie u.a. bei dem Upload von Berichten, dem Ausführen eines Aktualisierungsplans oder dem Löschen eines Ordners.

[!INCLUDE [GDPR-related guidance](../../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Komponenten einer REST-API-Anforderung/Antwort

Ein REST-API-Anforderung/Antwort-Paar kann in fünf Komponenten gegliedert werden:

* Der **Anforderungs-URI**, der aus `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}` besteht. Obwohl der Header der Anforderungsnachricht den Anforderungs-URI enthält, erwähnen wir ihn an dieser Stelle extra, da es für viele Sprachen und Frameworks erforderlich ist, diesen separat der Anforderungsnachricht zu entnehmen.

    * URI-Schema: gibt das Protokoll an, das zum Übertragen der Anforderung verwendet wird. Zum Beispiel: `http` oder `https`.
    * URI-Host: gibt den Domänennamen oder die IP-Adresse des Servers an, auf dem die REST-Dienstendpunkte gehostet werden. Zum Beispiel: `myserver.contoso.com`.
    * Ressourcenpfad: gibt die Ressource oder die Ressourcenauflistung an, die möglicherweise mehrere Segmente enthalten, die vom Dienst zur Bestimmung der Auswahl dieser Ressourcen verwendet werden. Beispielsweise kann `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` verwendet werden, um angegebene Eigenschaften für CatalogItem zu verwenden.
    * Abfragezeichenfolge (optional): stellt zusätzliche, einfache Parameter wie die API-Version oder die Kriterien der Ressourcenauswahl bereit.

* Nachrichtenheaderfelder mit HTTP-Anforderungen:

    * eine erforderliche [HTTP-Methode](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (ebenfalls unter den Bezeichnungen „Vorgang“ oder „Verb“ bekannt), über die der Dienst erfährt, welchen Vorgangstyp Sie anfordern; Reporting Services REST-APIs unterstützen die Methoden DELETE, GET, HEAD, PUT, POST und PATCH (Löschen, Abrufen, Kopfteil, Platzieren, Bereitstellen und Reparieren).
    * Zusätzliche optionale Headerfelder, die für den angegebenen URI und HTTP-Methode erforderlich sind.

* Optionale **Nachrichtentextfelder mit HTTP-Antworten** zur Unterstützung des URI und des HTTP-Vorgangs. Beispielsweise enthalten POST-Vorgänge MIME-codierte Objekte, die als komplexe Parameter übergeben werden. Für POST- oder PUT-Vorgänge sollte der MIME-codierte Textkörpertyp ebenfalls im Anforderungsheader `Content-type` angegeben werden. Einige Dienste verlangen die Verwendung eines MIME-Typs wie `application/json`.

* **Nachrichtenheaderfelder mit HTTP-Anworten**:

    * Ein [HTTP-Statuscode](http://www.w3.org/Protocols/HTTP/HTRESP.html), der zwischen den Erfolgscodes 2xx und den Fehlercodes 4xx oder 5xx liegt. Stattdessen kann auch, wie in der API-Dokumentation angegeben, ein Statuscode zurückgegeben werden, der für einen Dienst definiert ist.
    * Zusätzliche optionale Headerfelder, die zum Unterstützen der Antwort der Anforderung erforderlich sind, z.B. ein `Content-type`-Antwortheader.

* Optionale **Nachrichtentextfelder mit HTTP-Antworten**:

    * MIME-codierte Antwortobjekte werden im HTTP-Antworttext zurückgegeben, wie z.B. eine Antwort von einer GET-Methode, die Daten zurückgibt. Für gewöhnlich werden diese Objekte in einem strukturierten Format wie JSON oder XML zurückgegeben, wie im `Content-type`-Antwortheader angegeben.

## <a name="api-documentation"></a>API-Dokumentation

Eine moderne REST-API benötigt auch eine moderne API-Dokumentation. Die REST-API basiert auf der OpenAPI-Spezifikation (auch Swagger-Spezifikation genannt). Die Dokumentation ist unter [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0) verfügbar. Neben der API-Dokumentation finden Sie auf dem SwaggerHub auch Anweisungen zum Generieren einer Clientbibliothek in der Sprache Ihrer Wahl: JavaScript, TypeScript, C#, Java, Python, Ruby, usw.

## <a name="testing-api-calls"></a>Testen von API-Aufrufen

[Fiddler](https://www.telerik.com/fiddler) ist ein Tool zum Testen von HTTP-Anforderungs- bzw. Antwortnachrichten. Fiddler ist ein kostenloser Proxy zum Webdebuggen, der Ihre REST-Anforderungen abfangen kann. Dies vereinfacht die Diagnose von Anforderungs-bzw. Antwortnachrichten.

## <a name="next-steps"></a>Nächste Schritte

Prüfen Sie die verfügbaren APIs im [SwaggerHub](https://app.swaggerhub.com/api/microsoft-rs/SSRS/2.0).

Beispiele finden Sie auf dem[GitHub](https://github.com/Microsoft/Reporting-Services). Das Beispiel beinhaltet neben einem PowerShell-Beispiel eine HTML5-App, die auf TypeScript, React und Webpack basiert.

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)

---
title: ADO Security Design Issues | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, security
ms.assetid: 86b83a38-efdf-4831-a6d5-7e470d517d1c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64f4a22d849572d6e32006dbe997dd134e5c2e0d
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293126"
---
# <a name="ado-security-design-features"></a>ADO Security Design-Features
Den folgenden Abschnitten wird das Design von Sicherheitsfeatures in ActiveX Data Objects (ADO) 2.8 und höher. Diese Änderungen wurden in ADO 2.8 vorgenommen, um die Sicherheit zu verbessern. ADO 6.0, die in Windows DAC 6.0 in Windows Vista enthalten ist, ist funktionell gleichwertig mit ADO 2.8, die in MDAC 2.8 in Windows XP und Windows Server 2003 enthalten war. Dieses Thema enthält Informationen dazu, wie Sie Ihre Anwendungen in ADO 2.8 oder höher am besten schützen.

> [!IMPORTANT]
>  Wenn Sie Ihre Anwendung von einer früheren Version von ADO aktualisieren möchten, empfiehlt es sich, dass Sie die aktualisierte Anwendung auf einem Computer nicht für die Produktion testen, bevor Sie es für Kunden bereitstellen. Auf diese Weise können Sie sicherstellen, dass Sie Kompatibilitätsprobleme bekannt sind, bevor Sie die aktualisierte Anwendung bereitstellen.

## <a name="internet-explorer-file-access-scenarios"></a>Internet Explorer-Dateizugriffsszenarien
 Die folgenden Funktionen Auswirkungen wie ADO 2.8 und höher funktioniert, wenn es in verwendet wird, ein Skript erstellt Webseiten in Internet Explorer.

### <a name="revised-and-improved-security-warning-message-box-now-used-to-alert-users"></a>Überarbeitete und verbesserten Sicherheitsfunktionen Warnhinweisfeld jetzt verwendet, um Benutzer
 Für ADO 2.7 und frühere Versionen wird die folgende Warnmeldung angezeigt, wenn es sich bei eine skriptgesteuerte Webseite versucht, die ADO-Code von einem nicht vertrauenswürdigen Anbieter ausgeführt wird:

```console
This page accesses data on another domain. Do you want to allow this? To
avoid this message in Internet Explorer, you can add a secure Web site to
your Trusted Sites zone on the Security tab of the Internet Options dialog
box.
```

 Für ADO 2.8 und höher wird die genannte Meldung nicht mehr angezeigt. Stattdessen wird die folgende Meldung angezeigt, in diesem Kontext:

```console
This Website uses a data provider that may be unsafe. If you trust the
Website, click OK, otherwise click Cancel.
```

 Die genannte Meldung kann der Benutzer, während die Folgen für jede der beiden Optionen kennen, informierte Entscheidung zu treffen:

-   Wenn Benutzer die Website vertraut wird, klicken auf OK lässt alle Datenträger typsicherer Code (alle ADO-Methoden und Eigenschaften mit Ausnahme der den Datenträger zugegriffen werden kann APIs, die weiter unten in diesem Thema beschrieben) ausführen, und führen Sie im Browserfenster.

-   Wenn der Benutzer die Website nicht vertraut, blockiert das Klicken auf "Abbrechen" den ADO-Code für den Datenzugriff und vollständig ausgeführt.

### <a name="disk-accessible-code-limited-now-to-trusted-sites"></a>Datenträger zugegriffen werden kann Code jetzt zu vertrauenswürdigen Websites begrenzt
 Zusätzliche Änderungen wurden in ADO 2.8 vorgenommen, die die Fähigkeit von einem eingeschränkten Satz von APIs, insbesondere zu beschränken, die das Potenzial zu lesen oder Schreiben in Dateien auf dem lokalen Computer verfügbar machen können. Nachfolgend finden Sie die API-Methoden, die weitere wurden aus Sicherheitsgründen eingeschränkt werden, wenn Internet Explorer ausführen:

-   Für die ADO **Stream** Objekt, wenn die [LoadFromFile](../../ado/reference/ado-api/loadfromfile-method-ado.md) oder [SaveToFile](../../ado/reference/ado-api/savetofile-method.md) Methoden verwendet werden.

-   Für die ADO **Recordset** Objekt, wenn entweder die [speichern](../../ado/reference/ado-api/save-method.md) Methode oder der [öffnen](../../ado/reference/ado-api/open-method-ado-recordset.md) Methode, z. B., wenn entweder die **AdCmdFile** Option wird festgelegt, oder die [Microsoft OLE DB-Persistenz-Anbieter (MSPersist)](../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) verwendet wird.

 Für diese eingeschränkter Sätze von Funktionen mit potenziell Datenträger zugegriffen werden kann tritt ein, das folgende Verhalten für ADO 2.8 und höher, wenn Code, der diese Methoden verwendet, die in Internet Explorer ausgeführt wird:

-   Wenn der Standort, der der Code bereitgestellt, um die Liste der vertrauenswürdigen Sites Zone zuvor hinzugefügt wurde, wird der Code im Browser ausgeführt wird und Zugriff auf lokale Dateien.

-   Wenn der Standort nicht in der Liste der vertrauenswürdigen Sites Zone angezeigt wird, wird der Code ist gesperrt, und Zugriff auf lokale Dateien wird verweigert.

    > [!NOTE]
    >  In ADO 2.8 und höher wird der Benutzer nicht informiert oder sollten Sie die Liste der vertrauenswürdigen Sites Zone Websites hinzufügen. Aus diesem Grund ist die Verwaltung der Liste der vertrauenswürdigen Sites die Verantwortung für diejenigen bereitstellen oder Unterstützung von Website-basierte Anwendungen, die Zugriff auf das lokale Dateisystem erforderlich ist.

### <a name="access-blocked-to-the-activecommand-property-on-recordset-objects"></a>Zugriff blockiert, um die ActiveCommand-Eigenschaft für Recordset-Objekte
 Bei der Ausführung in Internet Explorer blockiert ADO 2.8 jetzt den Zugriff auf die [ActiveCommand](../../ado/reference/ado-api/activecommand-property-ado.md) -Eigenschaft für ein aktives **Recordset** Objekt und gibt einen Fehler zurück. Der Fehler tritt auf, unabhängig davon, ob die Seite angezeigt auf einer Website, die in der Liste der vertrauenswürdigen Sites registriert wird.

### <a name="changes-in-handling-for-ole-db-providers-and-integrated-security"></a>Änderungen bei der Verwendung von OLE DB-Anbieter und die integrierte Sicherheit
 Beim Überprüfen der ADO 2.7 und frühere Versionen für potenzielle Sicherheitsprobleme und Probleme, wurde das folgende Szenario ermittelt:

 In einigen Fällen ist die OLE DB-Anbieter, die die integrierte Sicherheit unterstützt [DBPROP_AUTH_INTEGRATED](https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx) Eigenschaft kann potenziell skriptgesteuerten Webseiten versehentlich zu anderen Servern herstellen ADO Connection-Objekt wiederverwenden zulassen verwenden die Anmeldeinformationen des aktuellen Benutzer. Behandeln OLE DB-Anbieter abhängig davon, wie sie ausgewählt haben oder nicht bereitgestellt werden, für die integrierte Sicherheit, um dies zu verhindern, ADO 2.8 und höher.

 Für Webseiten, die von Standorten, die in der Liste der Zone vertrauenswürdige Sites aufgelistet geladen werden, enthält die folgende Tabelle eine Aufschlüsselung der wie ADO 2.8 und höher ADO-Verbindungen in beiden Fällen verwaltet.

|IE-Einstellungen für die Benutzerauthentifizierung, anmelden|-Anbieter unterstützt werden "Integrated Security" und UID und PWD angegeben (SQLOLEDB)|Anbieter unterstützt "Integrated Security" (JOLT, MSDASQL, MSPersist) nicht.|-Anbieter unterstützt "Integrated Security" und SSPI (es werden keine Benutzer-ID/PWD angegeben) festgelegt ist|
|------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
|Automatisches Anmelden mit aktuellen Benutzernamen und Kennwort|Verbindung zulassen|Verbindung zulassen|Verbindung zulassen|
|Eingabeaufforderung für Benutzername und Kennwort|Verbindung zulassen|Fehlschlagen der Verbindung|Fehlschlagen der Verbindung|
|Automatisches Anmelden nur in der Intranetzone|Verbindung zulassen|Eingabeaufforderung für Benutzer mit der sicherheitswarnung|Eingabeaufforderung für Benutzer mit der sicherheitswarnung|
|Anonymous-Anmeldung|Verbindung zulassen|Fehlschlagen der Verbindung|Fehlschlagen der Verbindung|

 Im Fall, wo eine sicherheitswarnung jetzt angezeigt wird, informiert das Meldungsfeld Benutzer:

```console
This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.
```

 Die genannte Meldung ermöglicht den Benutzer eine fundiertere Entscheidung treffen und entsprechend fortgesetzt.

> [!NOTE]
>  Für nicht vertrauenswürdige Sites (d. h. Websites nicht in der Liste der Zone vertrauenswürdige Sites aufgelistet) Wenn der Anbieter auch (wie weiter oben in diesem Abschnitt erläutert) nicht vertrauenswürdig ist, kann der Benutzer zwei Sicherheitswarnungen in einer Zeile, die eine Warnung über den unsafe-Anbieter und eine zweite Warnung angezeigt, zu der Es wurde versucht, ihre Identität zu verwenden. Wenn der Benutzer auf die erste Warnung auf OK klickt, werden die Einstellungen von Internet Explorer und in der obigen Tabelle beschriebene Verhalten-Antwortcode ausgeführt.

## <a name="controlling-whether-password-text-is-returned-in-ado-connection-strings"></a>Steuern, ob Kennworttext in ADO-Verbindungszeichenfolgen zurückgegeben werden
 Wenn Sie versuchen, den Wert abzurufen der ["ConnectionString"](../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft für ein ADO **Verbindung** Objekts, die folgenden Ereignisse auftreten:

1.  Wenn die Verbindung geöffnet ist, wird ein Initialisierungsaufruf für den zugrunde liegenden OLE DB-Anbieter gesendet beim Abrufen der Verbindungszeichenfolge.

2.  Abhängig von der Einstellung in der OLE DB-Anbieter, der die [DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO](https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx) -Eigenschaft, die Kennwörter sind enthalten, zusammen mit anderen Verbindungsinformationen für die Zeichenfolge, die zurückgegeben wird.

 Z. B. wenn die dynamische Eigenschaft des ADO-Verbindung **Persist Security Info** nastaven NA hodnotu **"true"**, Kennwortinformationen befindet sich in der Verbindungszeichenfolge zurückgegeben. Andernfalls, wenn die Eigenschaft wurde auf der zugrunde liegenden Anbieter festgelegt **"false"** Kennwortinformationen fehlt (z. B. mit dem SQLOLEDB-Anbieter) in die zurückgegebene Zeichenfolge.

 Bei Verwendung von Drittanbieter-(, also nicht-Microsoft) OLE DB-Anbieter mit Ihrem Anwendungscode ADO, Sie können überprüfen, wie die **DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO** Eigenschaft wird implementiert, um zu bestimmen, ob Einbeziehung von Informationen zum Kennwort mit ADO-Verbindungszeichenfolgen ist zulässig.

## <a name="checking-for-non-file-devices-when-loading-and-saving-recordsets-or-streams"></a>Überprüfen für nicht-Datei-Geräte, die beim Laden und Speichern von Recordsets oder -streams
 Für ADO 2.7 und frühere Versionen, Dateieingabe/-Ausgabe Vorgänge wie z. B. [öffnen](../../ado/reference/ado-api/open-method-ado-recordset.md) und [speichern](../../ado/reference/ado-api/save-method.md) , der zum Lesen und Schreiben von dateibasierte Daten können in einigen Fällen ermöglichen eine URL oder Dateiname verwendet werden, die einen nicht auf einem Datenträger angegeben verwendet wurden Grundlage Dateityp an. Z. B. LPT1, COM2, PRN. TXT "," AUX kann als Alias für/-Ausgaben zwischen Drucker und zusätzliche Geräte auf dem System mit bestimmten verwendet werden

 Diese Funktionalität wurde für ADO 2.8 und höher aktualisiert. Zum Öffnen und speichern **Recordset** und **Stream** Objekten, die ADO führt jetzt eine typüberprüfung Datei, um sicherzustellen, dass das angegeben wird, einen URL-Zeichenfolge oder ein Eingabe- oder -Gerät eine tatsächliche Datei.

> [!NOTE]
>  Datei typüberprüfung gilt in diesem Abschnitt beschriebenen nur für Windows 2000 und höher. Es gilt nicht für Situationen, in denen ADO 2.8 oder höher unter früheren Versionen von Windows, z. B. Windows 98 ausgeführt wird.

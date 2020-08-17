---
description: ADO-Sicherheits Entwurfs Features
title: ADO-Sicherheits Entwurfs Probleme | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fc525a10d6211ee5f15517618f2cc5b99c8abee8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355396"
---
# <a name="ado-security-design-features"></a>ADO-Sicherheits Entwurfs Features
In den folgenden Abschnitten werden die Sicherheits Entwurfs Features in ActiveX Data Objects (ADO) 2,8 und höher beschrieben. Diese Änderungen wurden in ADO 2,8 vorgenommen, um die Sicherheit zu verbessern. ADO 6,0, das in Windows DAC 6,0 in Windows Vista enthalten ist, ist funktional äquivalent zu ADO 2,8, das in MDAC 2,8 in Windows XP und Windows Server 2003 enthalten war. Dieses Thema enthält Informationen zur optimalen Absicherung Ihrer Anwendungen in ADO 2,8 oder höher.

> [!IMPORTANT]
>  Wenn Sie Ihre Anwendung aus einer früheren Version von ADO aktualisieren, empfiehlt es sich, die aktualisierte Anwendung auf einem nicht Produktions Computer zu testen, bevor Sie Sie für Kunden bereitstellen. Auf diese Weise können Sie sicherstellen, dass Sie alle Kompatibilitätsprobleme kennen, bevor Sie die aktualisierte Anwendung bereitstellen.

## <a name="internet-explorer-file-access-scenarios"></a>Internet Explorer-Datei Zugriffs Szenarien
 Die folgenden Features wirken sich darauf aus, wie ADO 2,8 und höher funktioniert, wenn es in Skript gesteuerten Webseiten in Internet Explorer verwendet wird.

### <a name="revised-and-improved-security-warning-message-box-now-used-to-alert-users"></a>Das überarbeitete und verbesserte Sicherheits Warn Meldungs Feld wird jetzt zum Benachrichtigen von Benutzern verwendet.
 Bei ADO 2,7 und früher wird die folgende Warnmeldung angezeigt, wenn eine Skript gesteuerte Webseite versucht, ADO-Code von einem nicht vertrauenswürdigen Anbieter auszuführen:

```console
This page accesses data on another domain. Do you want to allow this? To
avoid this message in Internet Explorer, you can add a secure Web site to
your Trusted Sites zone on the Security tab of the Internet Options dialog
box.
```

 Bei ADO 2,8 und höher wird die vorherige Meldung nicht mehr angezeigt. Stattdessen wird die folgende Meldung in diesem Kontext angezeigt:

```console
This Website uses a data provider that may be unsafe. If you trust the
Website, click OK, otherwise click Cancel.
```

 Die vorherige Meldung ermöglicht dem Benutzer, fundierte Entscheidungen zu treffen, während er die Konsequenzen für beide Optionen kennt:

-   Wenn der Benutzer der Site vertraut, wird durch Klicken auf "OK" der gesamte Datenträger sichere Code (alle ADO-Methoden und-Eigenschaften, mit Ausnahme der auf Datenträger zugänglichen APIs, die weiter unten in diesem Thema beschrieben werden) für die Ausführung und Ausführung im Browserfenster zugelassen.

-   Wenn der Benutzer die Website nicht als vertrauenswürdig einstuft, wird durch Klicken auf "Abbrechen" der ADO-Code für den Datenzugriff blockiert und vollständig ausgeführt.

### <a name="disk-accessible-code-limited-now-to-trusted-sites"></a>Auf Datenträger zugänglicher Code ist jetzt auf vertrauenswürdige Sites beschränkt
 In ADO 2,8 wurden zusätzliche Entwurfs Änderungen vorgenommen, die die Fähigkeit einer begrenzten Gruppe von APIs einschränken, die möglicherweise das Lesen aus und Schreiben in Dateien auf dem lokalen Computer offenlegen. Im folgenden finden Sie die API-Methoden, die bei der Ausführung von Internet Explorer für die Sicherheit noch weiter eingeschränkt wurden:

-   Für das ADO- **Streamobjekt** , wenn die [LoadFromFile](../../ado/reference/ado-api/loadfromfile-method-ado.md) -Methode oder die [savedefile](../../ado/reference/ado-api/savetofile-method.md) -Methode verwendet wird.

-   Für das ADO- **Recordset** -Objekt, wenn entweder die [Save](../../ado/reference/ado-api/save-method.md) -Methode oder die [Open](../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode verwendet wird, z. b. wenn entweder die **adcmdfile** -Option festgelegt ist oder der Microsoft OLE DB Dauerhaftigkeits [Anbieter (MSPersist)](../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md) verwendet wird.

 Für diese begrenzten Sätze von potenziell Datenträger zugänglichen Funktionen tritt das folgende Verhalten bei ADO 2,8 und höher auf, wenn Code, der diese Methoden verwendet, in Internet Explorer ausgeführt wird:

-   Wenn die Site, die den Code bereitgestellt hat, zuvor zur Zone der vertrauenswürdigen Sites hinzugefügt wurde, wird der Code im Browser ausgeführt, und der Zugriff auf lokale Dateien wird gewährt.

-   Wenn die Site nicht in der Zonen Liste der vertrauenswürdigen Sites angezeigt wird, wird der Code blockiert, und der Zugriff auf lokale Dateien wird verweigert.

    > [!NOTE]
    >  In ADO 2,8 und höher wird der Benutzer nicht benachrichtigt, und es wird davon abgeraten, Websites zur Zone der vertrauenswürdigen Sites hinzuzufügen. Daher liegt die Verwaltung der Liste vertrauenswürdiger Sites in der Verantwortung derjenigen, die Website basierte Anwendungen bereitstellen oder unterstützen, die Zugriff auf das lokale Dateisystem benötigen.

### <a name="access-blocked-to-the-activecommand-property-on-recordset-objects"></a>Der Zugriff auf die ActiveCommand-Eigenschaft für Recordset-Objekte wurde blockiert.
 Bei der Ausführung in Internet Explorer blockiert ADO 2,8 nun den Zugriff auf die [ActiveCommand](../../ado/reference/ado-api/activecommand-property-ado.md) -Eigenschaft für ein aktives **Recordset** -Objekt und gibt einen Fehler zurück. Der Fehler tritt auf, unabhängig davon, ob die Seite von einer Website stammt, die in der Liste der vertrauenswürdigen Sites registriert ist.

### <a name="changes-in-handling-for-ole-db-providers-and-integrated-security"></a>Änderungen bei der Behandlung von OLE DB Anbietern und integrierter Sicherheit
 Beim Überprüfen von ADO 2,7 und früheren Versionen auf mögliche Sicherheitsprobleme und-Probleme wurde das folgende Szenario entdeckt:

 In einigen Fällen können OLE DB Anbieter, die die integrierte Sicherheits [DBPROP_AUTH_INTEGRATED](https://msdn.microsoft.com/library/windows/desktop/ms712973.aspx) Eigenschaft unterstützen, möglicherweise die Verwendung des ADO-Verbindungs Objekts durch Skript gesteuerte Webseiten erlauben, um unbeabsichtigt eine Verbindung mit anderen Servern herzustellen, indem die aktuellen Anmelde Informationen der Benutzer verwendet werden. Um dies zu verhindern, behandeln ADO 2,8 und höher OLE DB Anbieter, je nachdem, wie Sie für die integrierte Sicherheit bereitstellen oder nicht bereitstellen.

 Für Webseiten, die aus den in der Liste der vertrauenswürdigen Sites aufgeführten Websites geladen werden, finden Sie in der folgenden Tabelle eine Aufschlüsselung, wie ADO 2,8 und höher ADO-Verbindungen in jedem Fall verwaltet.

|IE-Einstellungen für die Benutzerauthentifizierung, Anmeldung|Der Anbieter unterstützt "integrierte Sicherheit" und UID und PWD werden angegeben (SQLOLEDB).|Der Anbieter unterstützt keine "integrierte Sicherheit" (Jolt, MSDASQL, MSPersist).|Der Anbieter unterstützt "integrierte Sicherheit", und er ist auf SSPI festgelegt (es wurden keine UID/pwd angegeben).|
|------------------------------------------------|----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
|Automatische Anmeldung mit aktuellem Benutzernamen und Kennwort|Verbindung zulassen|Verbindung zulassen|Verbindung zulassen|
|Eingabeaufforderung für Benutzername und Kennwort|Verbindung zulassen|Verbindung fehlschlagen|Verbindung fehlschlagen|
|Automatisches Anmelden nur in der Intranetzone|Verbindung zulassen|Benutzer mit Sicherheitswarnung auffordern|Benutzer mit Sicherheitswarnung auffordern|
|Anonyme Anmeldung|Verbindung zulassen|Verbindung fehlschlagen|Verbindung fehlschlagen|

 Wenn jetzt eine Sicherheitswarnung angezeigt wird, informiert das Meldungs Feld Benutzer:

```console
This Website is using your identity to access a data source. If you trust this Website, click OK, otherwise click Cancel.
```

 Die vorherige Meldung ermöglicht dem Benutzer, eine informierte Entscheidung zu treffen und entsprechend fortzufahren.

> [!NOTE]
>  Bei nicht vertrauenswürdigen Websites (d. h. Websites, die nicht in der Zonen Liste der vertrauenswürdigen Sites aufgeführt sind) gilt: Wenn der Anbieter ebenfalls nicht vertrauenswürdig ist (wie weiter oben in diesem Abschnitt erläutert), werden dem Benutzer möglicherweise zwei Sicherheitswarnungen in einer Zeile angezeigt, eine Warnung über den unsicheren Anbieter und eine zweite Warnung zum Versuch, seine Identität zu verwenden. Wenn der Benutzer zur ersten Warnung auf OK klickt, werden die in der obigen Tabelle beschriebenen Einstellungen für Internet Explorer-und Antwort Verhalten ausgeführt.

## <a name="controlling-whether-password-text-is-returned-in-ado-connection-strings"></a>Steuern der Rückgabe von Kenn Wort Text in ADO-Verbindungs Zeichenfolgen
 Wenn Sie versuchen, den Wert der [ConnectionString](../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft für ein ADO- **Verbindungs** Objekt zu erhalten, treten die folgenden Ereignisse auf:

1.  Wenn die Verbindung geöffnet ist, wird ein Initialisierungs Befehl an den zugrunde liegenden OLE DB Anbieter gerichtet, um die Verbindungs Zeichenfolge abzurufen.

2.  Abhängig von der Einstellung im OLE DB-Anbieter der [DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO](https://msdn.microsoft.com/library/windows/desktop/ms714905.aspx) -Eigenschaft werden Kenn Wörter zusammen mit anderen zurückgegebenen Verbindungs Zeichen folgen Informationen eingeschlossen.

 Wenn z. b. die dynamische Eigenschaft ADO-Verbindung persistente **Sicherheitsinformationen** auf **true**festgelegt ist, sind die Kenn Wort Informationen in der zurückgegebenen Verbindungs Zeichenfolge enthalten. Wenn der zugrunde liegende Anbieter die-Eigenschaft auf **false** festgelegt hat (z. b. mit dem SQLOLEDB-Anbieter), werden Kenn Wort Informationen in der zurückgegebenen Verbindungs Zeichenfolge ausgelassen.

 Wenn Sie Drittanbieter (d. h. nicht-Microsoft) OLE DB Anbietern mit Ihrem ADO-Anwendungscode verwenden, können Sie überprüfen, wie die **DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO** -Eigenschaft implementiert wird, um zu bestimmen, ob die Einbindung von Kenn Wort Informationen mit ADO-Verbindungs Zeichenfolgen zulässig ist.

## <a name="checking-for-non-file-devices-when-loading-and-saving-recordsets-or-streams"></a>Überprüfen auf nicht-Datei Geräte beim Laden und Speichern von Recordsets oder Streams
 Bei ADO 2,7 und früheren Versionen können Dateieingabe-/Ausgabevorgänge wie z. b. " [Öffnen](../../ado/reference/ado-api/open-method-ado-recordset.md) " und " [Speichern](../../ado/reference/ado-api/save-method.md) ", die zum Lesen und Schreiben von dateibasierten Daten verwendet wurden, in einigen Fällen die Verwendung einer URL oder eines Datei namens ermöglichen, der einen nicht auf einem Datenträger basierenden Dateityp Beispielsweise können LPT1, COM2, PRN.TXT, AUX als Alias für die Eingabe/Ausgabe zwischen Druckern und zusätzlichen Geräten im System verwendet werden, wobei bestimmte

 Bei ADO 2,8 und höher wurde diese Funktion aktualisiert. Zum Öffnen und Speichern von **Recordset** -und **Stream** -Objekten führt ADO nun eine Dateityp Überprüfung durch, um sicherzustellen, dass das in einer URL oder einem Dateinamen angegebene Eingabe-oder Ausgabegerät eine tatsächliche Datei ist.

> [!NOTE]
>  Die Dateityp Überprüfung, wie in diesem Abschnitt beschrieben, gilt nur für Windows 2000 und höher. Dies gilt nicht für Situationen, in denen ADO 2,8 oder höher unter früheren Windows-Versionen ausgeführt wird, wie z. b. Windows 98.

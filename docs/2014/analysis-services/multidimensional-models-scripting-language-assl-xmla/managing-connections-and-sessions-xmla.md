---
title: Verwalten von Verbindungen und Sitzungen (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statefulness [XML for Analysis]
- statelessness [XML for Analysis]
- XML for Analysis, sessions
- states [XML for Analysis]
- XMLA, sessions
- sessions [XML for Analysis]
ms.assetid: b83bb3ff-09be-4fda-9d1d-6248e04ffb21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3bbd5ef006674a61830bf07de31f73c3915b0d4e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62701997"
---
# <a name="managing-connections-and-sessions-xmla"></a>Verwalten von Verbindungen und Sitzungen (XMLA)
  *Status* Behaftung ist eine Bedingung, bei der der Server die Identität und den Kontext eines Clients zwischen Methoden aufrufen beibehält. Die *Status losigkeit* ist eine Bedingung, bei der der Server die Identität und den Kontext eines Clients nicht speichert, nachdem ein Methoden aufrufwerk abgeschlossen wurde.  
  
 Zum Bereitstellen von Status Behaftung werden von XML for Analysis (XMLA) *Sitzungen* unterstützt, mit denen eine Reihe von Anweisungen gleichzeitig ausgeführt werden kann. Ein Beispiel einer solchen Reihe von Anweisungen ist die Erstellung eines berechneten Elements, das in nachfolgenden Abfragen verwendet wird.  
  
 Im Allgemeinen folgen Sitzungen in XMLA dem folgenden Verhalten gemäß der Spezifikation OLE DB 2.6:  
  
-   Sitzungen definieren Transaktion und Befehlskontextbereich.  
  
-   Mehrere Befehle können im Kontext einer einzelnen Sitzung ausgeführt werden.  
  
-   Die Unterstützung für Transaktionen im XMLA-Kontext erfolgt über anbieterspezifische Befehle, die mit der [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methode gesendet werden.  
  
 XMLA definiert eine Möglichkeit zur Unterstützung von Sitzungen in einer Webumgebung, deren Modus Ähnlichkeit hat mit dem Zugang, der von dem DAV-Protokoll (Distributed Authoring and Versioning) für die Implementierung von Sperrungen in einer lose verbundenen Umgebung verwendet wird. Diese Implementierung entspricht DAV insofern, als der Anbieter die Möglichkeit hat, Sitzungen aus mehreren Gründen ablaufen zu lassen (beispielsweise bei Timeout oder Verbindungsfehlern). Wenn Sitzungen unterstützt werden, müssen Webdienste in der Lage sein, unterbrochene Befehlssätze, die neu gestartet werden müssen, zu verarbeiten.  
  
 Die Spezifikation des Simple Object Access Protocol (SOAP) des World Wide Web Consortium (W3C) empfiehlt die Verwendung von SOAP-Headern für die Erstellung von neuen Protokollen auf der Grundlage von SOAP-Nachrichten. In der folgenden Tabelle werden die SOAP-Headerelemente und -attribute aufgeführt, die XMLA für die Initiierung, Erhaltung und Beendigung von Sitzungen definiert.  
  
|SOAP-Header|Beschreibung|  
|-----------------|-----------------|  
|BeginSession|Dieser Header fordert bei dem Anbieter die Erstellung einer neuen Sitzung an. Der Anbieter sollte mit der Erstellung einer neuen Sitzung antworten und die Sitzungs-ID als Teil des Sitzungsheaders in der SOAP-Antwort zurückgeben.|  
|SessionID|Der Wertbereich enthält die Sitzungs-ID, die für den Rest der Sitzung in jedem Methodenaufruf verwendet werden muss. Der Anbieter sendet dieses Tag in der SOAP-Antwort, und der Client muss dieses Attribut ebenfalls mit jedem Sitzungsheaderelement senden.|  
|Sitzung|Dieser Header muss für jeden Methodenaufruf in der Sitzung verwendet werden, und die Sitzungs-ID muss im Wertbereich des Headers enthalten sein.|  
|EndSession|Verwenden Sie diesen Header, um die Sitzung zu beenden. Die Sitzungs-ID muss im Wertbereich enthalten sein.|  
  
> [!NOTE]  
>  Eine Sitzungs-ID garantiert nicht, dass eine Sitzung gültig bleibt. Wenn eine Sitzung abläuft (beispielsweise bei einem Timeout oder wenn die Verbindung verloren geht), kann der Anbieter die Aktionen der Sitzung beenden und rückgängig machen. Als Ergebnis führen alle nachfolgenden Methodenaufrufe des Clients mit der Sitzungs-ID zu einem Fehler, der angibt, dass die Sitzung ungültig ist. Ein Client sollte diese Bedingung handhaben können und in der Lage sein, die Methodenaufrufe der Sitzung von Anfang an erneut zu senden.  
  
## <a name="legacy-code-example"></a>Legacycodebeispiel  
 Im folgenden Beispiel wird gezeigt, wie Sitzungen unterstützt werden.  
  
1.  Fügen Sie dem ausgehenden XMLA-Methodenaufruf des Clients einen BeginSession-Header in SOAP hinzu, um eine Sitzung zu beginnen. Der Wertbereich ist zunächst leer, da die Sitzungs-ID noch nicht bekannt ist.  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  Die SOAP-Antwortnachricht vom Anbieter enthält die Sitzungs-ID im Bereich des Rückgabe Headers unter Verwendung des XMLA- \<Header Tags SessionID>.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  Für jeden Methodenaufruf in der Sitzung muss der Sitzungsheader hinzugefügt werden, der die vom Anbieter zurückgegebene Sitzungs-ID enthält.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  Wenn die Sitzung beendet ist, wird \<das EndSession->-Tag verwendet, das den zugehörigen Sitzungs-ID-Wert enthält.  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

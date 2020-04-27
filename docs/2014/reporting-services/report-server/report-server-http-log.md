---
title: Berichtsserver-HTTP-Protokoll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTTP [Reporting Services]
ms.assetid: 6cc433b7-165c-4b16-9034-79256dd6735f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ca3437315803ff8435640bf58219fe93f96e242a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103399"
---
# <a name="report-server-http-log"></a>Berichtsserver-HTTP-Protokoll
  Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Berichts Server-http-Protokolldateien behalten einen Datensatz für jede HTTP-Anforderung und-Antwort, die vom Berichts Server verarbeitet werden. Da Anforderungsüberlauf- und Timeoutfehler den Berichtsserver nicht erreichen, werden sie nicht in der Protokolldatei aufgezeichnet.  
  
 Die HTTP-Protokollierung ist standardmäßig nicht aktiviert. Um die HTTP-Protokollierung zu aktivieren, ändern Sie die Konfigurationsdatei **ReportingServicesService. exe. config** so, dass diese Funktion in der-Installation verwendet wird.  
  
## <a name="viewing-log-information"></a>Anzeigen von Protokollinformationen  
 Das Protokoll ist eine ASCII-Textdatei. Sie können die Datei mithilfe eines Text-Editors anzeigen. Die Berichtsserver-HTTP-Protokolldatei ist identisch mit der erweiterten W3C-Protokolldatei in IIS und verwendet ähnliche Felder, sodass Sie vorhandene IIS-Protokolldatei-Viewer zum Lesen der Berichtsserver-HTTP-Protokolldatei verwenden können. Die folgende Tabelle enthält weitere Informationen über die HTTP-Protokolldatei:  
  
|||  
|-|-|  
|**Dateiname**|Standardmäßig lauten die Namen der Protokolldateien<br /><br /> `ReportServerService_HTTP_<timestamp>.log.`<br /><br /> Sie können das Präfix des Dateinamens anpassen, indem Sie das HttpTraceFileName-Attribut in der Datei ReportingServicesService.exe.config ändern. Der Timestamp basiert auf der koordinierten Weltzeit (UTC).|  
|**Datei Speicherort**|Die Dateien werden an den folgenden Speicherort geschrieben:<br /><br /> `\Microsoft SQL Server\<SQL Server Instance>\Reporting Services\LogFiles`|  
|**Dateiformat**|Die Datei liegt im Format EN-US vor. Es handelt sich um eine ASCII-Textdatei.|  
|**Dateierstellung und -beibehaltung**|Das HTTP-Protokoll wird erstellt, nachdem Sie es in der Konfigurationsdatei aktiviert und den Dienst neu gestartet haben und der Berichtsserver eine HTTP-Anforderung verarbeitet hat. Wenn Sie die Einstellungen konfiguriert haben, die Protokolldatei jedoch nicht sehen können, öffnen Sie einen Bericht, oder starten Sie eine Berichtsserveranwendung (wie den Berichts-Manager), um eine HTTP-Anforderung zum Erstellen der Datei zu generieren.<br /><br /> Es wird ein neues Exemplar der Protokolldatei nach jedem Neustart des Diensts und einer nachfolgenden HTTP-Anforderung an den Berichtsserver erstellt.<br /><br /> Standardmäßig sind Ablaufverfolgungsprotokolle auf 32 Megabyte begrenzt und werden nach 14 Tagen gelöscht.|  
  
## <a name="configuration-settings-for-report-server-http-log"></a>Konfigurationseinstellungen für das Berichtsserver-HTTP-Protokoll  
 Um das Berichts Server-HTTP-Protokoll zu konfigurieren, verwenden Sie den Editor, um die Datei **ReportingServicesService. exe. config** zu ändern. Die Konfigurationsdatei befindet sich im Ordner \Programme\Microsoft SQL Server\MSSQL.n\Reporting Services\ReportServer\Bin.  
  
 Um den HTTP-Server zu aktivieren `http:4` , fügen Sie dem RStrace-Abschnitt der Datei ReportingServicesService. exe. config hinzu. Alle anderen HTTP-Protokolldateieinträge sind optional. Das folgende Beispiel umfasst alle Einstellungen, sodass Sie den gesamten Abschnitt über den Abschnitt RStrace kopieren und dann die nicht benötigten Einstellungen löschen können.  
  
```  
   <RStrace>  
         <add name="FileName" value="ReportServerService_" />  
         <add name="FileSizeLimitMb" value="32" />  
         <add name="KeepFilesForDays" value="14" />  
         <add name="Prefix" value="tid, time" />  
         <add name="TraceListeners" value="debugwindow, file" />  
         <add name="TraceFileMode" value="unique" />  
         <add name="HttpTraceFileName" value="ReportServerService_HTTP_" />  
         <add name="HttpTraceSwitches" value="date,time, clientip,username,serverip,serverport,host,method,uristem,uriquery,protocolstatus,bytesreceived,timetaken,protocolversion,useragent,cookiereceived,cookiesent,referrer" />  
         <add name="Components" value="all:3,http:4" />  
   </RStrace>  
```  
  
## <a name="log-file-fields"></a>Protokolldateifelder  
 In der folgenden Tabelle sind die im Protokoll verfügbaren Felder beschrieben. Die Feldliste kann konfiguriert werden; Sie können mit der `HTTPTraceSwitches`-Konfigurationseinstellung angeben, welche Felder einbezogen werden sollen. In der **Standard** Spalte wird angegeben, ob das Feld automatisch in die Protokolldatei aufgenommen werden soll, wenn `HTTPTraceSwitches`Sie nicht angeben.  
  
|Feld|BESCHREIBUNG|Standard|  
|-----------|-----------------|-------------|  
|HttpTraceFileName|Dieser Wert ist optional. Der Standardwert ist ReportServerServiceHTTP_. Sie können einen anderen Wert angeben, wenn Sie eine andere Dateinamenkonvention verwenden möchten. (Sie können zum Beispiel den Servernamen einbeziehen, wenn Protokolldateien zentral gespeichert werden).|Ja|  
|HTTPTraceSwitches|Dieser Wert ist optional. Wenn Sie diesen Wert angeben, können Sie die in der Protokolldatei verwendeten Felder im durch Trennzeichen getrennten Format konfigurieren.|Nein|  
|Date|Das Datum des Auftretens der Aktivität.|Nein|  
|Time|Die Uhrzeit des Auftretens der Aktivität.|Nein|  
|ClientIp|Die IP-Adresse des Clients, der auf den Berichtsserver zugreift.|Ja|  
|UserName|Der Name des Benutzers, der auf den Berichtsserver zugreift.|Nein|  
|ServerPort|Die für die Verbindung verwendete Portnummer.|Nein|  
|Host|Der Inhalt des Hostheaders.|Nein|  
|Methode|Die Aktion oder SOAP-Methode, die vom Client aufgerufen wird.|Ja|  
|UriStem|Die Ressource, auf die zugegriffen wird.|Ja|  
|UriQuery|Die Abfrage, mit der auf die Ressource zugegriffen wird.|Nein|  
|ProtocolStatus|Der HTTP-Statuscode.|Ja|  
|BytesReceived|Die Anzahl der vom Server empfangenen Bytes.|Nein|  
|TimeTaken|Die Zeit (in Millisekunden) von der Rückgabe der Anforderungsdaten durch HTTP.SYS bis zum Verarbeitungsende der letzten Sendung durch den Server ohne die Netzwerk-Übertragungszeit.|Nein|  
|ProtocolVersion|Die vom Client verwendete Protokollversion.|Nein|  
|UserAgent|Der vom Client verwendete Browsertyp.|Nein|  
|CookieReceived|Der Inhalt des vom Server empfangenen Cookies.|Nein|  
|CookieSent|Der Inhalt des vom Server gesendeten Cookies.|Nein|  
|Referrer|Die vorherige vom Client aufgerufene Website.|Nein|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsserverdienst-Ablaufverfolgungsprotokoll](report-server-service-trace-log.md)   
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  

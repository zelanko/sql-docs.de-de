---
title: Herstellen einer Verbindung Sybase (SybaseToSQL) mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0805246d5b88138cfa97019d1e0cd524c82456c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738073"
---
# <a name="connect-to-sybase-sybasetosql"></a>Herstellen einer Verbindung mit Sybase (SybaseToSQL)
Verwenden der **Herstellen einer Verbindung mit Sybase** im Dialogfeld Verbindung mit der Sybase Adaptive Server Enterprise (ASE)-Instanz, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Sybase**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung in Sybase**.  
  
## <a name="options"></a>Tastatur  
**Anbieter**  
Wählen Sie einen von der installierten Anbieter auf dem Computer, für die Verbindung mit der Sybase-Servers.  
  
**Mode**  
Wählen Sie entweder standard oder die erweiterte Verbindungsmodus. Im Modus "standard" Geben Sie ein oder wählen Sie Werte für den Servernamen, Port, Benutzername und Kennwort. Im erweiterten Modus geben Sie eine Verbindungszeichenfolge an.  
  
**Servername**  
Geben Sie an, oder wählen Sie den Namen oder die IP-Adresse des Servers, Adaptive. Der Standardservername ist identisch mit den Namen des Computers. Dies ist ein Modus "standard"-Option.  
  
**Serverport**  
Wenn Sie einen nicht standardmäßigen Port für Verbindungen mit der ASE verwenden, geben Sie die Portnummer ein. Die Standardportnummer ist 5000. Dies ist ein Modus "standard"-Option.  
  
**Benutzername**  
Geben Sie den Benutzernamen, der Verbindung mit der ASE verwendet wird. Dies ist ein Modus "standard"-Option.  
  
**Kennwort**  
Geben Sie das Kennwort für den Benutzernamen ein. Dies ist ein Modus "standard"-Option.  
  
**Verbindungszeichenfolge**  
Geben Sie die vollständige Verbindungszeichenfolge für die Verbindung, die ASE ein.  
  
Verbindungszeichenfolgen werden von Name-Wert-Paaren bestehen. Die Namen der Parameter variieren je nach den genutzten Anbieter.  
  
**Verbindungsparameter für die verschiedenen Anbietern sind wie folgt aus:**  
  
1.  Verbindungsparameter für den **OLE DB-Anbieter**  
  
    |Einstellung|Sybase 12,5-Parameter|Sybase-15-Parameter|  
    |-----------|-------------------------|-----------------------|  
    |Servername|Servername|Server|  
    |Port|Server-Port-Adresse|Port|  
    |Benutzername|Benutzer-ID|Benutzer-ID|  
    |Kennwort|Kennwort|Kennwort|  
    |Anbieter|Anbieter|Anbieter|  
  
    Für Sybase ASE 12,5 ist eine Beispiel-Verbindungszeichenfolge wie folgt:  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Für Sybase ASE-15 ist eine Beispiel-Verbindungszeichenfolge wie folgt:  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Verbindungsparameter für den **ODBC-Anbieter**  
  
    |Einstellung|Sybase 12,5/15-Parameter|  
    |-----------|-----------------------------|  
    |Treibername|Treiber|  
    |Servername|Server|  
    |Benutzername|Benutzer-ID|  
    |Kennwort|PWD|  
    |Portnummer|Port|  
  
    Für Sybase ASE 12,5 oder 15 ist eine Beispiel-Verbindungszeichenfolge wie folgt:  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Verbindungsparameter für den **ADO.NET-Anbieter**  
  
    |Einstellung|Sybase 12,5/15-Parameter|  
    |-----------|-----------------------------|  
    |Servername|Server|  
    |Benutzername|Benutzer-ID|  
    |Kennwort|PWD|  
    |Portnummer|Port|  
  
    Ein Beispiel für die Verbindungszeichenfolge für die ADO NET-Anbieter ist wie folgt:  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Weitere Informationen finden Sie in der ASE-Dokumentation.  
  
Dies ist eine erweiterte Option aus.  
  

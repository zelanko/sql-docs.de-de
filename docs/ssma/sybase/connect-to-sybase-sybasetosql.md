---
title: Herstellen einer Verbindung mit Sybase (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6cb2f4196737cceec2f60684de1b7409f5e383a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083395"
---
# <a name="connect-to-sybase-sybasetosql"></a>Herstellen einer Verbindung mit Sybase (SybaseToSQL)
Verwenden Sie das Dialogfeld **mit Sybase verbinden** , um eine Verbindung mit der Instanz von Sybase Adaptive Server Enterprise (ASE) herzustellen, die Sie migrieren möchten.  
  
Um auf dieses Dialogfeld zuzugreifen, wählen Sie im Menü **Datei** die Option **mit Sybase verbinden**aus. Wenn Sie bereits eine Verbindung hergestellt haben, stellt der Befehl **erneut eine Verbindung mit Sybase**her.  
  
## <a name="options"></a>Tastatur  
**Anbieter**  
Wählen Sie einen der installierten Anbieter auf dem Computer aus, um eine Verbindung mit dem Sybase-Server herzustellen.  
  
**Mode**  
Wählen Sie entweder den Modus Standard oder erweiterte Verbindung aus. Im Standardmodus geben Sie Werte für Servername, Port, Benutzername und Kennwort ein, oder wählen Sie Sie aus. Im erweiterten Modus geben Sie eine Verbindungs Zeichenfolge an.  
  
**Servername**  
Geben Sie den Namen oder die IP-Adresse des adaptiven Servers ein, oder wählen Sie diesen Der Standard Servername ist identisch mit dem Computernamen. Dies ist eine Standardmodus-Option.  
  
**Serverport**  
Wenn Sie einen nicht standardmäßigen Port für Verbindungen mit ASE verwenden, geben Sie die Portnummer ein. Die Standard Portnummer ist 5000. Dies ist eine Standardmodus-Option.  
  
**Benutzername**  
Geben Sie den Benutzernamen ein, der zum Herstellen der Verbindung mit der ASE verwendet wird. Dies ist eine Standardmodus-Option.  
  
**Kennwort**  
Geben Sie das Kennwort für den Benutzernamen ein, Dies ist eine Standardmodus-Option.  
  
**Verbindungszeichenfolge**  
Geben Sie die vollständige Verbindungs Zeichenfolge für die Verbindung mit ASE ein.  
  
Verbindungs Zeichenfolgen bestehen aus Parameter Name-Wert-Paaren. Die Parameternamen variieren je nach verwendeter Anbieter.  
  
**Die Verbindungsparameter für verschiedene Anbieter lauten wie folgt:**  
  
1.  Verbindungsparameter für **OLE DB-Anbieter**  
  
    |Einstellung|Sybase 12,5-Parameter|Sybase 15-Parameter|  
    |-----------|-------------------------|-----------------------|  
    |Servername|Servername|Server|  
    |Port|Server Port Adresse|Port|  
    |Benutzername|Benutzer-ID|Benutzer-ID|  
    |Kennwort|Kennwort|Kennwort|  
    |Anbieter|Anbieter|Anbieter|  
  
    Für Sybase ASE 12,5 lautet die folgende Beispiel Verbindungs Zeichenfolge:  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Für Sybase ASE 15 lautet eine Beispiel-Verbindungs Zeichenfolge wie folgt:  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Verbindungsparameter für **ODBC-Anbieter**  
  
    |Einstellung|Parameter Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Treibername|Trei|  
    |Servername|Server|  
    |Benutzername|UID|  
    |Kennwort|PWD|  
    |Portnummer|Port|  
  
    Für Sybase-ASE 12,5 oder 15 lautet die folgende Beispiel Verbindungs Zeichenfolge:  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Verbindungsparameter für **ADO.NET-Anbieter**  
  
    |Einstellung|Parameter Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Servername|Server|  
    |Benutzername|UID|  
    |Kennwort|PWD|  
    |Portnummer|Port|  
  
    Ein Beispiel für die Verbindungs Zeichenfolge für den ADO.NET-Anbieter lautet wie folgt:  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Weitere Informationen finden Sie in der ASE-Dokumentation.  
  
Dies ist eine Option für den erweiterten Modus.  
  

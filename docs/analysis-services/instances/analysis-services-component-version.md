---
title: Überprüfen Sie die Build-Version des kumulativen Updates für SQL Server Analysis Services | Microsoft-Dokumentation
ms.date: 07/11/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b1da8384bb51360178e1735d13f6c6b706e8b7ff
ms.sourcegitcommit: 87efa581f7d4d84e9e5c05690ee1cb43bd4532dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38999353"
---
# <a name="verify-analysis-services-cumulative-update-build-version"></a>Überprüfen Sie die Build-Version des kumulativen Updates für Analysis Services

Ab SQL Server 2017, stimmen die Buildversionsnummer der Analysis Services und SQL Server-Datenbank-Engine-Buildversionsnummer nicht überein. Obwohl Analysis Services und Datenbank-Engine den gleichen Installer verwenden, die Buildsysteme jeweils sind getrennt.

 In einigen Fällen kann es erforderlich sein, überprüfen, ob ein buildpaket kumulativen Update (CU) angewendet wurde und Analysis Services-Komponenten aktualisiert wurden. Sie können überprüfen, durch Vergleichen der Versionsnummern von Build von Analysis Services-Komponentendateien, die mit den Versionsnummern von Build für eine bestimmte CU auf Ihrem Computer installiert werden soll.

## <a name="verify-component-file-version"></a>Überprüfen Sie die Datei Komponentenversion

Zu Datei-Version der Komponente zu überprüfen, 

1. Wechseln Sie zu [SQL Server 2017-Buildversionen](https://support.microsoft.com/help/4047329). 
2. In **builds von SQL Server 2017 Kumulatives Update (CU)**, klicken Sie auf die **Knowledge Base-Anzahl** für den Build, die Sie überprüfen möchten.
3. In der **kumulative Update (#) für SQL Server 2017** Artikel, in der **Paketinformationen kumulative Update** Bereich, erweitern Sie **Kumulatives Update Paket-Dateiinformationen**.
4. In der **SQL Server 2017 Analysis Services** table, überprüfen Sie die Dateiversion für die **msmdsrv.exe** Komponentendatei. Wenn die CU angewendet wurde, sollte die Dateiversionsnummer der msmdsrv.exe-Datei, die auf Ihrem Computer installiert überein.

## <a name="see-also"></a>Siehe auch  

[Installieren von SQL Server-Wartungsupdates](../../database-engine/install-windows/install-sql-server-servicing-updates.md)  

[Update Center für Microsoft SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)
  
  

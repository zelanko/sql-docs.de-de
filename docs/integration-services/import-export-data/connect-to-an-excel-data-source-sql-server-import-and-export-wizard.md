---
title: Herstellen einer Verbindung mit einer Excel-Datenquelle (SQL Server-Import/Export-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 747cf2bb865fb9b3fcdb11a43e410f574556dcc5
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723895"
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Herstellen einer Verbindung mit einer Excel-Datenquelle (SQL Server-Import/Export-Assistent)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


In diesem Artikel wird erläutert, wie Sie eine Verbindung mit einer **Microsoft Excel**-Datenquelle über die Seiten **Datenquelle auswählen** oder **Ziel auswählen** des SQL Server-Import/Export-Assistenten herstellen.

Der folgende Screenshot zeigt eine Beispielverbindung mit einer Microsoft Excel-Arbeitsmappe.

![Excel-Verbindung](../../integration-services/import-export-data/media/excel-connection.png) 

Sie müssen möglicherweise zusätzliche Dateien herunterladen und installieren, um eine Verbindung mit Excel-Dateien herzustellen. Weitere Informationen finden Sie unter [Get the files you need to connect to Excel (Herunterladen von Dateien zum Herstellen einer Verbindung mit Excel)](../load-data-to-from-excel-with-ssis.md#files-you-need).

> [!IMPORTANT]
> Ausführliche Informationen über das Herstellen einer Verbindung mit Excel-Dateien sowie Einschränkungen und bekannte Probleme beim Laden von Daten aus oder in Excel-Dateien finden Sie unter [Load data from or to Excel with SQL Server Integration Services (SSIS) (Laden von Daten aus oder in Excel mit SQL Server Integration Services (SSIS))](../load-data-to-from-excel-with-ssis.md).

## <a name="options-to-specify"></a>Anzugebende Optionen

> [!NOTE]
> Die Verbindungsoptionen für diesen Datenanbieter bleiben stets unverändert – egal, ob Excel die Quelle oder das Ziel ist. Das bedeutet, dass die angezeigten Optionen auf den Seiten **Datenquelle auswählen** und **Ziel auswählen** des Assistenten gleich sind.

**Excel-Dateipfad**  
 Geben Sie den Pfad und den Dateinamen für die Excel-Datei an. Beispiel:
-   Für eine Datei auf dem lokalen Computer können Sie beispielsweise **C:\\MeineDaten.xlsx** festlegen.
-   Für eine Datei auf einer Netzwerkfreigabe können Sie beispielsweise **\\\\Verkauf\\Datenbank\\Northwind.xlsx** festlegen.

Oder klicken Sie auf **Durchsuchen**.  
  
 **Durchsuchen**  
 Suchen Sie die Kalkulationstabelle mithilfe des Dialogfelds **Öffnen**.  

> [!NOTE]
> Der Assistent kann keine kennwortgeschützte Excel-Datei öffnen.

 **Excel-Version**  
Wählen Sie die Version von Excel aus, die von der Quelle oder Zielarbeitsmappe verwendet wird.

**Erste Zeile enthält Spaltennamen**  
Geben Sie an, ob die erste Datenzeile Spaltennamen enthält.
-   Wenn die Daten keine Spaltennamen enthalten, Sie diese Option jedoch aktivieren, behandelt der Assistent die erste Zeile der Quelldaten wie Spaltennamen.
-   Wenn die Daten Spaltennamen enthalten, Sie diese Option jedoch deaktivieren, behandelt der Assistent die Zeile mit den Spaltennamen als erste Datenzeile.

Wenn Sie festlegen, dass die Daten keine Spaltennamen enthalten, verwendet der Assistent F1, F2 usw. als Spaltenüberschriften.

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel wird in der Liste der Datenquellen nicht angezeigt
Wenn Excel nicht in der Liste der Datenquellen angezeigt wird, sollten Sie überprüfen, ob Sie die 64-Bit-Version des Assistenten verwenden. Die Anbieter für Excel und Access sind in der Regel 32-Bit-Versionen und werden in der 64-Bit-Version des Assistenten nicht angezeigt. Führen Sie stattdessen die 32-Bit-Version des Assistenten aus.

> [!NOTE]
> Sie müssen SQL Server installieren, um die 64-Bit-Version des SQL Server-Import/Export-Assistenten verwenden zu können. SQL Server Data Tools (SSDT) und SQL Server Management Studio (SSMS) sind 32-Bit-Anwendungen und installieren daher auch nur 32-Bit-Dateien, einschließlich der 32-Bit-Version des Assistenten.

## <a name="see-also"></a>Siehe auch
[Load data from or to Excel with SQL Server Integration Services (SSIS) (Laden von Daten aus oder in Excel mit SQL Server Integration Services (SSIS))](../load-data-to-from-excel-with-ssis.md)  
[Auswählen einer Datenquelle](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Auswählen eines Ziels](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


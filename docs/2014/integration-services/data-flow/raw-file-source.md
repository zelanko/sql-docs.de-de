---
title: Rohdatendatei-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 53b9b4a38e82fe37f0f1f114969f2f71fb4848a8
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431537"
---
# <a name="raw-file-source"></a>Rohdatendatei-Quelle
  Die Rohdatendatei-Quelle liest Rohdaten aus einer Datei. Die Darstellung der Daten erfolgt im systemeigenen Quellformat, sodass die Daten nicht übersetzt und fast nicht analysiert werden müssen. Dies bedeutet, dass die Rohdatendatei-Quelle Daten schneller als andere Quellen, wie z. B. Flatfile- und OLE DB-Quellen, lesen kann.  
  
 Mithilfe der Rohdatendatei-Quelle werden Rohdaten abgerufen, die zuvor vom Rohdatendatei-Ziel geschrieben wurden. Sie können die Rohdatendatei-Quelle auch auf eine leere Rohdatendatei verweisen, die nur die Spalten (Nur-Metadatendatei) enthält. Sie verwenden das Rohdatendatei-Ziel, um die Nur-Metadatendatei zu generieren, ohne das Paket ausführen zu müssen. Weitere Informationen finden Sie unter [Raw File Destination](raw-file-destination.md).  
  
 Das Format der Rohdatendatei enthält Sortierungsinformationen: Das Rohdatendatei-Ziel speichert alle Sortierungsinformationen, einschließlich der Vergleichsflags für Zeichenfolgenspalten. Die Rohdatendatei-Quelle liest und beachtet die Sortierungsinformationen. Sie können die Rohdatendatei-Quelle dergestalt konfigurieren, dass die Sortierflags in der Datei mit dem erweiterten Editor ignoriert werden. Weitere Informationen zu Vergleichsflags finden Sie unter [Comparing String Data](comparing-string-data.md).  
  
 Zum Konfigurieren der Rohdatendatei geben Sie den Namen der Datei an, die die Rohdatendatei-Quelle liest.  
  
> [!NOTE]  
>  Für diese Quelle wird kein Verbindungs-Manager verwendet.  
  
 Diese Quelle erzeugt nur eine Ausgabe. Eine Fehlerausgabe wird nicht unterstützt.  
  
## <a name="configuration-of-the-raw-file-source"></a>Konfiguration der Rohdatendatei-Quelle  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Common Properties](../common-properties.md)  
  
-   [Benutzerdefinierte Eigenschaften der Rohdatendatei](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Informationen zum Festlegen der Eigenschaften der Komponente finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Blogeintrag, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), auf sqlservercentral.com  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rohdatendatei-Ziel](raw-file-destination.md)   
 [Datenfluss](data-flow.md)  
  
  

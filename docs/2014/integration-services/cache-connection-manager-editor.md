---
title: Cacheverbindungs-Manager-Editor | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.cacheconnection.f1
ms.assetid: 0d8f9324-0c35-4eea-b06d-da3cc2426d2c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: af7696c1d5194af721b6ff803736193db0285b8b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62771727"
---
# <a name="cache-connection-manager-editor"></a>Editor für den Cacheverbindungs-Manager
  Der Cacheverbindungs-Manager liest ein Verweisdataset aus der Cachetransformation oder einer Cachedatei (.caw) und kann die Daten in einer Cachedatei speichern. Die Daten werden immer im Arbeitsspeicher abgelegt.  
  
> [!NOTE]  
>  Der Cacheverbindungs-Manager unterstützt die BLOB-Datentypen (Binary Large Object) DT_TEXT, DT_NTEXT und DT_IMAGE nicht. Wenn das Verweisdataset einen BLOB-Datentyp enthält, schlägt die Komponente fehl, wenn Sie das Paket ausführen. Sie können den **Cacheverbindungs-Manager-Editor** verwenden, um Spaltendatentypen zu ändern.  
  
 Die Transformation für Suche führt Suchvorgänge im Verweisdataset aus.  
  
 Das Dialogfeld **Editor für den Cacheverbindungs-Manager** schließt die folgenden Registerkarten ein:  
  
-   [Registerkarte "Allgemein"](#generaltab)  
  
-   [Registerkarte "Spalten"](#columnstab)  
  
 Weitere Informationen zum Cacheverbindungs-Manager finden Sie unter [Cache Connection Manager](connection-manager/cache-connection-manager.md).  
  
##  <a name="generaltab"></a> Registerkarte Allgemein  
 Geben Sie auf der Registerkarte **Allgemein** des Dialogfelds **Editor für den Cacheverbindungs-Manager** an, ob der Cache aus einer Datei gelesen werden soll oder ob der Cache in einer Datei gespeichert werden soll.  
  
### <a name="options"></a>Optionen  
 **Name des Verbindungs-Managers**  
 Geben Sie einen eindeutigen Namen für die Cacheverbindung im Workflow an. Der angegebene Name wird im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer angezeigt.  
  
 **Beschreibung**  
 Beschreiben Sie die Verbindung. Die bewährte Methode ist hierbei, die Verbindung zweckbezogen zu beschreiben, sodass Pakete selbsterklärend und leichter zu verwalten sind.  
  
 **Dateicache verwenden**  
 Geben Sie an, ob eine Cachedatei verwendet werden soll.  
  
> [!NOTE]  
>  Die Schutzebene des Pakets gilt nicht für die Cachedatei. Wenn die Cachedatei vertrauliche Informationen enthält, schränken Sie den Zugriff auf den Speicherort oder Ordner, in dem Sie die Datei speichern, mithilfe einer Zugriffssteuerungsliste ein. Sie sollten nur bestimmten Konten den Zugriff ermöglichen. Weitere Informationen finden Sie unter [Zugriff auf Dateien, die von Paketen verwendet werden](../../2014/integration-services/access-to-files-used-by-packages.md).  
  
 Wenn Sie den Cacheverbindungs-Manager für die Verwendung einer Cachedatei konfigurieren, führt der Verbindungs-Manager eine der folgenden Aktionen aus:  
  
-   Speichern der Daten in einer Datei, wenn eine Cachetransformation so konfiguriert ist, dass Daten aus einer Datenquelle im Datenfluss in den Cacheverbindungs-Manager geschrieben werden. Weitere Informationen finden Sie unter [Cache Transform](data-flow/transformations/cache-transform.md).  
  
-   Lesen von Daten aus der Cachedatei  
  
 **Dateiname**  
 Geben Sie den Pfad und Dateinamen der Cachedatei ein.  
  
 **Durchsuchen**  
 Suchen Sie die Cachedatei.  
  
 **Metadaten aktualisieren**  
 Löschen Sie die Spaltenmetadaten im Cacheverbindungsmanager, und füllen Sie den Cacheverbindungs-Manager erneut mit Spaltenmetadaten aus einer bestimmten Cachedatei auf.  
  
##  <a name="columnstab"></a> Registerkarte 'Spalten'  
 Auf der Registerkarte **Spalten** des Dialogfelds **Editor für den Cacheverbindungs-Manager** können Sie die Eigenschaften jeder Spalte im Cache konfigurieren.  
  
### <a name="options"></a>Optionen  
 **Column**  
 Geben Sie den Spaltennamen an.  
  
 **Indexposition**  
 Geben Sie an, welche Spalten Indexspalten sind, indem Sie die Indexposition jeder Spalte angeben. Der Index ist eine Auflistung einer oder mehrerer Spalten.  
  
 Für Nicht-Index-Spalten ist die Indexposition 0.  
  
 Für Indexspalten ist die Indexposition eine fortlaufende positive Zahl. Diese Zahl gibt die Reihenfolge an, in der die Suchtransformation Zeilen im Verweisdataset mit Zeilen der Eingabedatenquelle vergleicht. Die Spalte mit den meisten eindeutigen Werten sollte die niedrigste Indexposition aufweisen.  
  
> [!NOTE]  
>  Wenn die Transformation für Suche so konfiguriert ist, dass sie einen Cacheverbindungs-Manager verwendet, können nur Indexspalten im Verweisdataset Eingabespalten zugeordnet werden. Auch müssen alle Indexspalten zugeordnet werden.  
  
 **Typ**  
 Geben Sie den Datentyp der Spalte an.  
  
 `Length`  
 Gibt den Datentyp der Spalte an. Wenn für den Datentyp zutreffend, können Sie den Wert von `Length` aktualisieren.  
  
 `Precision`  
 Gibt die Genauigkeit für bestimmte Spaltendatentypen an. Genauigkeit gibt die Anzahl der Ziffern einer Zahl an. Wenn für den Datentyp zutreffend, können Sie den Wert von `Precision` aktualisieren.  
  
 `Scale`  
 Gibt die Dezimalstellen für bestimmte Spaltendatentypen an. Dezimalstellen gibt die Anzahl der Nachkommastellen an. Wenn für den Datentyp zutreffend, können Sie den Wert von `Scale` aktualisieren.  
  
 `Code Page`  
 Gibt die Codepage für den Spaltentyp an. Wenn für den Datentyp zutreffend, können Sie den Wert von `Code Page` aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Lookup Transformation](data-flow/transformations/lookup-transformation.md)  
  
  

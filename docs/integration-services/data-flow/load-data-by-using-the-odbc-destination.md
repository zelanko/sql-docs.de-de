---
title: Laden von Daten mithilfe des ODBC-Ziels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 339ec0a8-922e-48c0-97b3-fc5ee34f95e3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 71852015f9595e51c61f0840ebcec6e41431a660
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941410"
---
# <a name="load-data-by-using-the-odbc-destination"></a>Laden von Daten mithilfe des ODBC-Ziels

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  In diesem Verfahren wird veranschaulicht, wie Sie Daten mithilfe des ODBC-Ziels laden. Das Paket muss bereits mindestens einen Datenflusstask und eine Quelle enthalten, damit Sie ein ODBC-Ziel hinzufügen und konfigurieren können.  
  
### <a name="to-load-data-using-an-odbc-destination"></a>So laden Sie Daten mithilfe eines ODBC-Ziels  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]das gewünschte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket.  
  
2.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**das ODBC-Ziel auf die Entwurfsoberfläche.  
  
3.  Ziehen Sie eine verfügbare Ausgabe einer Datenflusskomponente in den Eingabebereich des ODBC-Ziels.  
  
4.  Doppelklicken Sie auf das ODBC-Ziel.  
  
5.  Wählen Sie im Dialogfeld **Ziel-Editor für ODBC** auf der Seite **Verbindungs-Manager** einen vorhandenen ODBC-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um einen neuen Verbindungs-Manager zu erstellen.  
  
6.  Wählen Sie die Datenzugriffsmethode aus.  
  
    -   **Tabellenname – Batch**: Wählen Sie diese Option aus, um das ODBC-Ziel im Batchmodus zu konfigurieren. Wenn Sie diese Option aktivieren, können Sie die **Batchgröße**festlegen.  
  
    -   **Tabellenname – Zeile für Zeile**: Wählen Sie diese Option aus, um das ODBC-Ziel so zu konfigurieren, dass jede Zeile einzeln in die Zieltabelle eingefügt wird. Wenn Sie diese Option aktivieren, werden die Daten zeilenweise in die Tabelle geladen.  
  
7.  Wählen Sie in der Liste im Feld **Name der Tabelle oder Sicht** eine verfügbare Tabelle oder Sicht aus der Datenbank aus, oder geben Sie einen regulären Ausdruck zum Identifizieren der Tabelle ein. Diese Liste enthält nur die ersten 1000 Tabellen. Wenn die Datenbank mehr als 1000 Tabellen enthält, können Sie den Anfang eines Tabellennamens eingeben oder das Platzhalterzeichen (*) verwenden, um einen beliebigen Teil des Namens einzugeben und die gewünschten Tabellen anzuzeigen.  
  
8.  Sie können auf **Vorschau** klicken, um bis zu 200 Zeilen der Daten für die auf dem ODBC-Ziel ausgewählte Tabelle anzuzeigen.  
  
9. Klicken Sie auf **Zuordnungen** , und ordnen Sie Spalten aus der Liste **Verfügbare Eingabespalten** Spalten in der Liste **Verfügbare Zielspalten** zu, indem Sie Spalten von einer Liste in eine andere Liste ziehen.  
  
10. Klicken Sie auf **Fehlerausgabe**, um die Fehlerausgabe zu konfigurieren.  
  
11. Klicken Sie auf **OK**.  
  
12. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziel-Editor für ODBC &#40;Verbindungs-Manager-Seite&#41;](../../integration-services/data-flow/odbc-destination-editor-connection-manager-page.md)   
 [Ziel-Editor für ODBC &#40;Seite Zuordnungen&#41;](../../integration-services/data-flow/odbc-destination-editor-mappings-page.md)   
 [Quellen-Editor für ODBC &#40;Seite Fehlerausgabe&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  

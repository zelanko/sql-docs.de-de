---
title: Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1b3696612ab9d0693b3c0135b6aff34137906b7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107312"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a>Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services (Berichts-Generator und SSRS)
  Um eine MDX-Abfrage von einer [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle zu parametrisieren, müssen Sie der Abfrage einen Abfrageparameter hinzufügen. Im MDX-Abfrage-Designer können Sie im Entwurfsmodus und im Abfragemodus einen Abfrageparameter hinzufügen, indem Sie einen Filter angeben. Nachdem Sie die Abfrage mit einem Abfrageparameter definiert haben, erstellt Reporting Services automatisch einen Berichtsparameter und ein Dataset für die Bereitstellung der Liste mit gültigen Werten. Dies ermöglicht einem Benutzer, einen Wert anzugeben, der direkt an die Abfrage übergeben wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a>So definieren Sie in MDX im Entwurfsmodus einen Abfrageparameter  
  
1.  Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf ein Dataset, das aus dem Datenquellentyp [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt wurde, und klicken Sie dann auf **Abfrage**. Der MDX-Abfrage-Designer wird im Entwurfsmodus geöffnet.  
  
2.  Ziehen Sie eine Dimension in den Filterbereich, und legen Sie sie in der ersten Zelle in der Spalte **Dimension** ab.  
  
3.  Wählen Sie in der Spalte **Hierarchie** einen Wert aus der Dropdownliste aus.  
  
4.  Wählen Sie in der Spalte **Operator** einen Operator für die Dropdownliste aus.  
  
5.  Wählen Sie in der Spalte **Filterausdruck** einzelne Werte aus der Dropdownliste aus, oder klicken Sie auf das Element **Alle** , um alle Werte auszuwählen.  
  
6.  Aktivieren Sie in der Spalte **Parameter** das Kontrollkästchen, um einen Berichtsparameter zu erstellen.  
  
7.  Klicken Sie auf **Ausführen**.  
  
     Klicken Sie nach dem Ausführen der Abfrage auf der Symbolleiste auf **Entwurf** , um für die Ansicht der erstellten MDX-Abfrage in den Abfragemodus zu wechseln. Ändern Sie den Abfragetext im Abfragemodus nicht, falls Sie die Abfrage weiterhin im Entwurfsmodus entwickeln möchten. Klicken Sie auf **Entwurf** , um zurück in den Entwurfsmodus zu wechseln.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Erweitern Sie im Bereich Berichtsdatenbereich den Parameterknoten, um den Berichtsparameter anzuzeigen, der automatisch für den Filter erstellt wurde.  
  
     Um das Dataset anzuzeigen, das verfügbare Werte für den Berichtsparameter enthält, klicken Sie mit der rechten Maustaste auf einen leeren Bereich im Berichtsdatenbereich, und klicken Sie dann auf **Ausgeblendete Datasets anzeigen**. Der Berichtsdatenbereich zeigt alle Datasets im Bericht an.  
  
### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a>So definieren Sie einen Abfrageparameter in MDX im Abfragemodus  
  
1.  Klicken Sie im Berichtsdatenbereich mit der rechten Maustaste auf ein Dataset, das aus dem Datenquellentyp [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] erstellt wurde, und klicken Sie dann auf **Abfrage**. Der MDX-Abfrage-Designer wird im Entwurfsmodus geöffnet.  
  
2.  Klicken Sie auf der Symbolleiste auf **Entwurf** , um in den Abfragemodus zu wechseln.  
  
3.  Klicken Sie auf der MDX-Abfrage-Designer-Symbolleiste auf **Abfrageparameter** (![Symbol für das Dialogfeld Abfrageparameter](../../analysis-services/media/iconqueryparameter.gif "Symbol für das Dialogfeld Abfrageparameter")). Das Dialogfeld Abfrageparameter wird geöffnet.  
  
4.  Klicken Sie in der Spalte **Parameter** auf **\<Parameter eingeben>**, und geben Sie dann den Namen eines Parameters ein.  
  
5.  Wählen Sie in der Spalte **Dimension** einen Wert aus der Dropdownliste aus.  
  
6.  Wählen Sie in der Spalte **Hierarchie** einen Wert aus der Dropdownliste aus.  
  
7.  Aktivieren Sie in der Spalte **Mehrere Werte** das Kontrollkästchen, um einen mehrwertigen Parameter zu erstellen.  
  
8.  Wählen Sie in der Spalte **Standard** entsprechend Ihrer Auswahl in Schritt 5 einzelne oder mehrere Werte aus der Dropdownliste aus.  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
10. Klicken Sie auf der Symbolleiste des Abfrage-Designers auf **Ausführen**.  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Erweitern Sie im Bereich Berichtsdatenbereich den Parameterknoten, um den Berichtsparameter anzuzeigen, der automatisch für den Filter erstellt wurde.  
  
     Um das Dataset anzuzeigen, das verfügbare Werte für den Berichtsparameter enthält, klicken Sie mit der rechten Maustaste auf einen leeren Bereich im Berichtsdatenbereich, und klicken Sie dann auf **Ausgeblendete Datasets anzeigen**. Der Berichtsdatenbereich zeigt alle Datasets im Bericht an.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Verbindungstyp für MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)   
 [Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services](analysis-services-mdx-query-designer-user-interface.md)  
  
  

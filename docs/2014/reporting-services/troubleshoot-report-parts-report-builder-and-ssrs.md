---
title: Problembehandlung bei Berichtsteilen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 58de4bd8c12bf4ac9551260ac3ba27b5888dce90
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56288518"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a>Problembehandlung bei Berichtsteilen (Berichts-Generator und SSRS)
  Die folgenden Tipps können beim Arbeiten mit Berichtsteilen hilfreich sein.  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a>Warum sehen mein Kollege und ich verschiedene Instanzen des gleichen Berichtsteils, wenn wir danach suchen?  
 Es kann mehrere Instanzen eines einzelnen Berichtsteils auf einem Berichtsserver oder auf einer SharePoint-Website geben, die in einen Berichtsserver integriert ist, und alle Instanzen haben den gleichen Globally Unique Identifier (GUID). Nur die aktuelle Instanz wird in der Liste der Suchergebnisse angezeigt. In einigen Situationen können verschiedene Instanzen eines einzelnen Berichtsteils unterschiedliche Berechtigungen aufweisen. Wenn Ihr Kollege und Sie über verschiedene Berechtigungen für den Server verfügen, sehen Sie beide nicht die gleiche Instanz. Nehmen Sie zum Beispiel einmal an, dass mehrere Exemplare eines Berichtsteils, die alle den gleichen GUID haben, in unterschiedlichen Ordnern auf einem Berichtsserver im integrierten SharePoint-Modus gespeichert werden. Wenn die Ordner unterschiedliche Berechtigungen aufweisen, dann haben die Berichtsteile in diesen Ordnern ebenfalls andere Berechtigungen.  
  
 Fragen Sie Ihren Berichtsserveradministrator, wenn Sie nicht wissen, über welche Berechtigungen Sie und Ihr Kollege verfügen.  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a>Wenn ich nach Berichtsteilen suche, die ich auf einen SharePoint-Server hochgeladen habe, sehe ich sie nicht. Warum nicht?  
 Berichtsteile, die Sie manuell in eine SharePoint-Dokumentbibliothek hochgeladen haben, anstatt sie mit Berichts-Generator zu veröffentlichen, werden möglicherweise nicht im Berichtsteilkatalog angezeigt. Der Berichtsserver, der für die Katalogsuche verwendet wird, muss möglicherweise mit dem Inhalt der SharePoint-Dokumentbibliothek synchronisiert werden. Weitere Informationen finden Sie unter [Aktivieren der Synchronisierung Berichtsserverdateien in der SharePoint-Zentraladministration](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) auf "MSDN.Microsoft.com".  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a>Warum können andere kein Bild in ihren Berichten sehen?  
 Wenn Sie einen Berichtsteil veröffentlichen, der ein Link zu einer Bilddatei ist, ist der Berichtsteil wirklich nur ein Link. Wenn andere das Bild auch dann nicht sehen können, wenn sie ihren Berichten das Bildberichtsteil hinzufügen, haben sie möglicherweise keine Berechtigungen für das verknüpfte Bild.  
  
 Es gibt einige mögliche Lösungen dafür:  
  
-   Erstellen Sie die Bilddatei als einen Berichtsteil, anstatt den Link zur Bilddatei als Berichtsteil zu verwenden.  
  
-   Verschieben Sie die Bilddatei an einen Speicherort, für den andere Berechtigungen haben.  
  
-   Bitten Sie den Berichtsserveradministrator, die Berechtigungen zu ändern.  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a>Warum erhalte ich eine "Zirkelverweis"-Fehlermeldung, wenn ich versuche, meinen Berichtsteil zu veröffentlichen?  
 Wenn Berichtselemente einen Zirkelverweis aufweisen, können Sie diese nicht als Berichtsteile veröffentlichen. Ein Berichtselement verweist beispielsweise auf ein Dataset, das wiederum auf einen Parameter verweist. Der Parameter verweist wiederum ebenfalls auf das Dataset. Sie müssen zuerst einen der Verweise löschen, bevor Sie den Berichtsteil veröffentlichen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsteile &#40;Berichts-Generator und SSRS&#41;](report-parts-report-builder-and-ssrs.md)  
  
  

---
title: Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0378394c274e66d71eebd642188f20194d29236b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65480006"
---
# <a name="create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy
  Sie verwenden in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]das Tool MDSModelDeploy, um ein Paket zu erstellen. Abhängig von den angegebenen Befehlen kann das Paket folgenden Inhalt haben:  
  
-   Nur Modellobjekte.  
  
-   Modellobjekte und Daten.  
  
 Wenn Sie ein Paket bereitstellen möchten, das nur Modellobjekte enthält, können Sie stattdessen den Modellbereitstellungs-Assistenten in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] -Webanwendung verwenden. Weitere Informationen finden Sie unter [Erstellen eines Modellbereitstellungspakets mithilfe des Assistenten](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md).  
> [!NOTE]  
> Diese Version des mdsmodelbereitstellungs-Tools kann nicht mehr als Gigabyte (GB) Arbeitsspeicher verwenden. Wenn Sie große Modelle mithilfe der Option **Modell Objekte und Daten** erstellen oder bereitstellen, tritt möglicherweise der Fehler "nicht genügend Arbeitsspeicher" oder "der Stream war zu lang" auf. Um dieses Problem zu beheben, verwenden Sie das MDS-Staging zum Bereitstellen der Daten. oder führen Sie ein Upgrade auf MDS 2016 oder eine höhere Version durch, einschließlich der aktualisierten Version des mdsmodelbereitstellungs-Tools.
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
1.  Die grundlegenden Berechtigungen zum Ausführen des MDSModelDeploy-Tools lauten wie folgt:  
  
    -   Die gleiche Windows-Berechtigung wie der MDS-Konfigurations-Manager (Windows-Administrator)  
  
    -   DBA-Berechtigung für die MDS-Datenbank  
  
2.  Die grundlegenden Berechtigungen zum Erstellen des Pakets mit dem MDSModelDeploy-Tool lauten wie folgt:  
  
    -   MDS-Modelladministratorberechtigung für das Datenmodell.  
  
    -   Funktionsberechtigung für das MDS-Integrationsmanagement  
  
3.  Die grundlegenden Berechtigungen zum Bereitstellen eines Modells mit dem MDSModelDeploy-Tool lauten wie folgt:  
  
    -   Funktionsberechtigung für den MDS-Explorer  
  
    -   Funktions Berechtigung für die MDS-Integrations Verwaltung  
  
    -   Funktionsberechtigung für die MDS-Systemverwaltung  
  
4.  Die grundlegenden Berechtigungen zum Auflisten von Modellen mit dem MDSModelDeploy-Tool lauten wie folgt:  
  
    -   Funktionsberechtigung für den MDS-Explorer  
  
    -   MDS-Modelladministratorberechtigung für das Datenmodell zum Anzeigen des Modells in der Liste.  
  
 Es muss ein Modell vorhanden sein, aus dem Sie ein Paket erstellen können. Weitere Informationen finden Sie unter [Erstellen eines Modells &#40;Master Data Services&#41;](create-a-model-master-data-services.md).  
  
 Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-model-deployment-package-by-using-mdsmodeldeploy"></a>So erstellen Sie ein Modellbereitstellungspaket mit MDSModelDeploy  
  
1.  Öffnen Sie eine Eingabeaufforderung.  
  
2.  Navigieren Sie zum Speicherort von "MDSModelDeploy.exe".  
  
    -   Wenn MDS am Standard Speicherort installiert wurde, befindet sich die Datei unter *Laufwerk*: \Programme\Microsoft SQL server\120\master Data services\configuration.  
  
    -   Wenn MDS nicht am Standardspeicherort installiert wurde, suchen Sie auf dem lokalen Computer nach der Datei "MDSModelDeploy.exe".  
  
3.  Optional. Dient zum Anzeigen der Optionen und der Hilfe.  
  
    -   Geben Sie `MDSModelDeploy` ein, und drücken Sie EINGABETASTE, um alle verfügbaren Optionen anzuzeigen.  
  
    -   Geben Sie Folgendes ein, um Hilfe für eine Option anzuzeigen, wobei *OptionName* der Name der Option ist: `MDSModelDeploy help OptionName`.  
  
4.  Optional. Wenn Sie über mehrere Webanwendungen verfügen, bestimmen Sie den Namen des Diensts, für den Sie die Bereitstellung durchführen, indem Sie diesen Befehl eingeben und die EINGABETASTE drücken:  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     Eine Liste von Werten wird zurückgegeben, z. B. `MDS1, Default Web Site, MDS`. Der erste Wert in dieser Liste (in diesem Fall `MDS1`) wird benötigt, um das Modell bereitzustellen.  
  
5.  Geben Sie Folgendes ein, um ein Paket zu erstellen, das Modellobjekte und Daten enthält. Dabei gilt: *ModelName*, *VersionName*, *ServiceName*und *PackageName* sind die Namen des Modells, der Version, des Diensts bzw. der PKG-Ausgabedatei:  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     Wenn Sie keine Daten einschließen möchten, verwenden Sie nicht die Schalter `-version` und `-includedata` .  
  
6.  Drücken Sie die EINGABETASTE. Nach der erfolgreichen Erstellung des Pakets wird eine Meldung angezeigt, die besagt, dass der MDSModelDeploy-Vorgang erfolgreich abgeschlossen wurde.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Bereitstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Modell Bereitstellungs Optionen &#40;Master Data Services&#41;](../../2014/master-data-services/model-deployment-options-master-data-services.md)   
 [Bereitstellen von Modellen &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
  

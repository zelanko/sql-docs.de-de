---
title: Installieren von Analysis Services im tabellarischen Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bf1a8ee0d5dd3dde585a027fd08fd833fb40304
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079912"
---
# <a name="install-analysis-services-in-tabular-mode"></a>Installieren von Analysis Services im Tabellenmodus
  Wenn Sie Analysis Services installieren, um die neuen Tabellenmodellierungsfunktionen zu verwenden, müssen Sie Analysis Services in einem Servermodus installieren, der diesen Modelltyp unterstützt. Der Servermodus ist "Tabellarisch" und wird während der Installation konfiguriert.  
  
 Nach der Installation des Servers in diesem Modus können Sie ihn zum Hosten von Projektmappen nutzen, die Sie im Designer für tabellarische Modelle erstellen. Ein Server im tabellarischen Modus ist erforderlich, um den Zugriff auf Daten im tabellarischen Modell über das Netzwerk zu ermöglichen.  
  
 Sie können den Modus "Tabellarisch" im Installations-Assistenten oder in einem Befehlszeilensetup angeben. Diese Vorgehensweisen werden in den nächsten Abschnitten beschrieben.  
  
## <a name="installation-wizard"></a>Installations-Assistent  
 Die folgende Liste enthält die Seiten im SQL Server-Installations-Assistenten, die zum Installieren von Analysis Services im tabellarischen Modus verwendet werden:  
  
1.  Wählen Sie in der Funktionsstruktur des Setups **Analysis Services** aus.  
  
     ![Setup-Funktionsstruktur mit Funktionsstruktur Services](../../../sql-server/install/media/ssas-setupas.gif "Funktionsstruktur Dienste mit Setup-Funktionsstruktur")  
  
2.  Auf der Seite Analysis Services-Konfiguration müssen Sie auswählen **im tabellarischen Modus**.  
  
     ![Setupseite mit Analysis Services-Konfigurationsoptionen](../../../sql-server/install/media/ssas-setupasconfig.gif "Setupseite mit Analysis Services-Konfigurationsoptionen")  
  
 Der tabellarische Modus verwendet die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq). Dies ist der Standardspeicher für tabellarische Modelle, die Sie in Analysis Services bereitstellen. Nachdem Sie Projektmappen mit einem tabellarischen Modell auf dem Server bereitgestellt haben, können Sie selektiv tabellarische Projektmappen konfigurieren, um DirectQuery-Festplattenspeicher als Alternative zu arbeitsspeichergebundenem Speicher zu verwenden.  
  
## <a name="command-line-setup"></a>Befehlszeilensetup  
 Das SQL Server-Setup enthält einen neuen Parameter (`ASSERVERMODE`), der den Servermodus angibt. Das folgende Beispiel zeigt ein Befehlszeilensetup, bei dem Analysis Services im tabellarischen Servermodus installiert wird.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 `INSTANCENAME` muss kürzer als 17 Zeichen sein.  
  
 Alle Platzhalterkontowerte müssen durch gültige Konten und Kennwörter ersetzt werden.  
  
 Mit der angegebenen Beispielbefehlszeilensyntax werden keine Tools, z. B. SQL Server Management Studio oder [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], installiert. Weitere Informationen zum Hinzufügen von Funktionen finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 Bei `ASSERVERMODE` wird die Groß- und Kleinschreibung beachtet.  Alle Werte müssen in Großbuchstaben angegeben werden. In der folgenden Tabelle werden die gültigen Werte für `ASSERVERMODE` beschrieben.  
  
|Wert|Description|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|Dies ist der Standardwert. Wenn Sie `ASSERVERMODE` nicht festlegen, wird der Server im multidimensionalen Servermodus installiert.|  
|POWERPIVOT|Dieser Wert ist optional. Wenn Sie den `ROLE`-Parameter festlegen, wird der Servermodus automatisch auf 1 festgelegt. Hierdurch wird `ASSERVERMODE` für eine PowerPivot für SharePoint-Installation optional. Weitere Informationen finden Sie unter [Installieren von PowerPivot über die Eingabeaufforderung](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).|  
|TABULAR|Dieser Wert ist erforderlich, wenn Sie Analysis Services mit einem Befehlszeilensetup im tabellarischen Modus installieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Konfigurieren von Speicherinternem oder DirectQuery-Zugriff für eine Datenbank für tabellarische Modelle](../../tabular-models/enable-directquery-mode-in-ssms.md)   
 [Tabellarische Modellierung &#40;SSAS – tabellarisch&#41;](../../tabular-models/tabular-models-ssas.md)  
  
  

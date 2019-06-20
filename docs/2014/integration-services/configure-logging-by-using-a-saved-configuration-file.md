---
title: Konfigurieren der Protokollierung mithilfe einer gespeicherten Konfigurationsdatei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- logs [Integration Services], containers
ms.assetid: e5fdbbcb-94ca-4912-aa7c-0d89cebbd308
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b2adc326ef2e0bb593b0532a51a9a677821ae0e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66060587"
---
# <a name="configure-logging-by-using-a-saved-configuration-file"></a>Konfigurieren der Protokollierung mithilfe einer gespeicherten Konfigurationsdatei
  In diesem Verfahren wird beschrieben, wie die Protokollierung für neue Container in einem Paket konfiguriert wird, indem eine zuvor gespeicherte Protokollierungskonfigurationsdatei geladen wird.  
  
 Alle Container in einem Paket verwenden standardmäßig dieselbe Protokollierungskonfiguration wie der übergeordnete Container. Die Tasks in einer Foreach-Schleife verwenden z. B. dieselbe Protokollierungskonfiguration wie die Foreach-Schleife.  
  
### <a name="to-configure-logging-for-a-container"></a>So konfigurieren Sie die Protokollierung für einen Container  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Klicken Sie im Menü **SSIS** auf **Protokollierung**.  
  
3.  Erweitern Sie die Paketbaumansicht, und wählen Sie den zu konfigurierenden Container aus.  
  
4.  Wählen Sie auf der Registerkarte **Anbieter und Protokolle** die Protokolle aus, die Sie für den Container verwenden möchten.  
  
    > [!NOTE]  
    >  Sie können Protokolle nur auf Paketebene erstellen. Weitere Informationen finden Sie unter [Aktivieren der Paketprotokollierung in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
5.  Klicken Sie auf die Registerkarte **Details** und dann auf **Laden**.  
  
6.  Suchen Sie die zu verwendende Protokollierungskonfigurationsdatei, und klicken Sie auf **Öffnen**.  
  
7.  Wählen Sie optional einen anderen zu protokollierenden Protokolleintrag aus, indem Sie das entsprechende Kontrollkästchen in der Spalte **Ereignisse** aktivieren. Klicken Sie auf **Erweitert** , um den für diesen Eintrag zu protokollierenden Informationstyp auszuwählen.  
  
    > [!NOTE]  
    >  Der neue Container enthält u. U. weitere Protokolleinträge, die für den Container nicht verfügbar sind, der ursprünglich zum Erstellen der Protokollierungskonfiguration verwendet wurde. Diese zusätzlichen Protokolleinträge müssen manuell ausgewählt werden, falls diese protokolliert werden sollen.  
  
8.  Um die aktualisierte Version der Protokollierungskonfiguration zu speichern, klicken Sie auf **Speichern**.  
  
9. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Protokollierung &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  

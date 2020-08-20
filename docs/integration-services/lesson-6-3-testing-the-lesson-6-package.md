---
description: 'Lektion 6.3: Testen des Pakets aus Lektion 6'
title: 'Schritt 3: Testen des Pakets aus Lektion 6 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6fc7b150f94d0f857244587140fd54b8fe7d38c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487723"
---
# <a name="lesson-6-3-test-the-lesson-6-package"></a>Lektion 6.3: Testen des Pakets aus Lektion 6

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]


Zur Laufzeit erhält Ihr Paket den Wert für die Eigenschaft **Verzeichnis** vom **VarFolderName**-Parameter.  
  
Um zu überprüfen, ob die **Directory**-Eigenschaft vom Paket aktualisiert wird, führen Sie das Paket aus. Da Sie drei Beispieldatendateien in das neue Verzeichnis kopiert haben, wird der Datenfluss dreimal ausgeführt.
  
## <a name="check-the-package-layout"></a>Überprüfen des Paketlayouts  
Bevor Sie das Paket testen, überprüfen Sie, ob Ablaufsteuerung und Datenfluss im Paket aus Lektion 6 den in den folgenden Abbildungen dargestellten Objekten ähneln.   
  
**Ablaufsteuerung**  
  
![Ablaufsteuerung](../integration-services/media/task4lesson2control.gif "Ablaufsteuerung")  
  
**Datenfluss**  
  
![Datenfluss](../integration-services/media/task5lesson5data.gif "Datenfluss")  
  
## <a name="test-the-lesson-6-package"></a>Testen des Pakets aus Lektion 6  
  
1.  Wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.  
  
2.  Klicken Sie nach dem Ausführen des Pakets im Menü **Debuggen** auf **Stop Debugging** (Debuggen beenden).  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 4: Bereitstellen des Pakets aus Lektion 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
  

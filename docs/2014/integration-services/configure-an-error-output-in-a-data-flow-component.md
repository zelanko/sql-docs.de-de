---
title: Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Integration Services], data flow components
- components [Integration Services], data flow
- error outputs [Integration Services]
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 03e93be67cdaba636edf9be0c0a33abc12e3700b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047451"
---
# <a name="configure-an-error-output-in-a-data-flow-component"></a>Konfigurieren einer Fehlerausgabe in einer Datenflusskomponente
  Viele Datenflusskomponenten unterstützen Fehlerausgaben, und [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer bietet je nach Komponente unterschiedliche Möglichkeiten für die Konfiguration einer Fehlerausgabe. Sie können nicht nur eine Fehlerausgabe, sondern auch die Spalten einer Fehlerausgabe konfigurieren. Dies schließt das Konfigurieren der von der Komponente hinzugefügten Spalten **ErrorCode** und **ErrorColumn** ein.  
  
## <a name="configuring-an-error-output"></a>Konfigurieren einer Fehlerausgabe  
 Zum Konfigurieren einer Fehlerausgabe stehen Ihnen zwei Optionen zur Verfügung:  
  
-   Verwenden des Dialogfelds **Fehlerausgabe konfigurieren** . Sie können dieses Dialogfeld zum Konfigurieren einer Fehlerausgabe für jede Datenflusskomponente verwenden, die eine Fehlerausgabe unterstützt.  
  
-   Verwenden des Editordialogfelds für die Komponente. Die Fehlerausgaben können bei einigen Komponenten direkt in ihrem Editordialogfeld konfiguriert werden. Es ist jedoch nicht möglich, Fehlerausgaben im Editordialogfeld für die ADO NET-Quelle, die Transformation für das Importieren von Spalten, die Transformation für OLE DB-Befehl oder das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact-Ziel zu konfigurieren.  
  
 Im Folgenden wird die Verwendung dieser Dialogfelder zum Konfigurieren von Fehlerausgaben beschrieben.  
  
#### <a name="to-configure-an-error-output-using-the-configure-error-output-dialog-box"></a>So konfigurieren Sie eine Fehlerausgabe mit dem Dialogfeld "Fehlerausgabe konfigurieren"  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Datenfluss** .  
  
4.  Ziehen Sie die Fehlerausgabe, dargestellt durch einen roten Pfeil, von der Komponente, die die Fehlerquelle darstellt, zu einer anderen Komponente im Datenfluss.  
  
5.  Wählen Sie im Dialogfeld **Fehlerausgabe konfigurieren** eine Aktion in den Spalten **Fehler** und **Abschneiden** für jede Spalte der Komponenteneingabe.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
#### <a name="to-add-an-error-output-using-the-editor-dialog-box-for-the-component"></a>So fügen Sie eine Fehlerausgabe mit dem Editordialogfeld für die Komponente hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Datenfluss** .  
  
4.  Doppelklicken Sie auf die Datenflusskomponenten, für die Sie eine Fehlerausgabe konfigurieren möchten, und führen Sie je nach Komponente einen der folgenden Schritte durch:  
  
    -   Klicken Sie auf **Fehlerausgabe konfigurieren**.  
  
    -   Klicken Sie auf **Fehlerausgabe**.  
  
5.  Legen Sie für jede Spalte die Option **Fehler** fest.  
  
6.  Legen Sie für jede Spalte die Option **Abschneiden** fest.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
## <a name="configuring-error-output-columns"></a>Konfigurieren von Fehlerausgabespalten  
 Verwenden Sie die Registerkarte **Eingabe- und Ausgabeeigenschaften** im Dialogfeld **Erweiterter Editor** zum Konfigurieren von Fehlerausgabespalten.  
  
#### <a name="to-configure-error-output-columns"></a>So konfigurieren Sie Fehlerausgabespalten  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf die Registerkarte **Datenfluss** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die Komponente, deren Fehlerausgabespalten Sie konfigurieren möchten, und klicken Sie auf **Erweiterten Editor anzeigen**.  
  
5.  Klicken Sie auf die Registerkarte **Eingabe- und Ausgabeeigenschaften**, und erweitern Sie **\<Komponentenname> Fehlerausgabe** und dann **Ausgabespalten**.  
  
6.  Klicken Sie auf eine Spalte, und aktualisieren Sie ihre Eigenschaften.  
  
    > [!NOTE]  
    >  Die Liste mit den Spalten enthält die Spalten in der Komponenteneingabe, die durch vorherige Fehlerausgaben hinzugefügten Spalten **ErrorCode** und **ErrorColumn** sowie die von dieser Komponente hinzugefügten Spalten **ErrorCode** und **ErrorColumn** .  
  
7.  Klicken Sie auf **OK.**  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehlerbehandlung in Daten](data-flow/error-handling-in-data.md)  
  
  
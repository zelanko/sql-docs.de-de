---
title: Überprüfen und Generieren ergänzender Protokollierungsskripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- scripts
ms.assetid: 5c858ae2-37d6-42e8-a252-7f6ed4e628a7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 68aa51facd21ec09be78e6ad0996131a9ee3cc5b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62835337"
---
# <a name="review-and-generate-supplemental-logging-scripts"></a>Überprüfen und Generieren ergänzender Protokollierungsskripts
  Verwenden Sie die Registerkarte **Skripts** , um ein Skript für die Oracle-Quelldatenbank auszuführen bzw. erneut auszuführen, mit dem die ergänzende Protokollierung eingerichtet wird.  
  
 Wählen Sie vor dem Ausführen der Skripts eine der folgenden Optionen:  
  
 **Include changes in this session**  
 Wählen Sie diese Option, um das Skript für alle neuen Tabellen auszuführen, die der CDC-Instanz hinzugefügt wurden, oder für Tabellen, die mit dem Eigenschaften-Editor geändert wurden.  
  
> [!NOTE]  
>  Wenn an den Tabellen in der CDC-Instanz keine Änderungen vorgenommen wurden, ist der Bereich des ergänzenden Oracle-Protokollierungsskripts leer.  
  
 **Include all tables/capture instances**  
 Wählen Sie diese Option, um das Skript für alle Tabellen und Aufzeichnungsinstanzen in der CDC-Instanz auszuführen.  
  
 Führen Sie das ergänzende Protokollierungsskript aus, nachdem Sie eine dieser Optionen ausgewählt haben.  
  
### <a name="to-run-the-supplemental-logging-scripts"></a>So führen Sie die ergänzenden Protokollierungsskripts aus  
  
1.  Klicken Sie auf **Run Script** , um das ergänzende Protokollierungsskript für die Tabellen auszuführen, die für die CDC-Instanz definiert sind. Dieses Skript weist die Oracle-Datenbank an, beim Protokollieren von UPDATE-Vorgängen zu aufgezeichneten Tabellen alle wichtigen Spalten in ihre Transaktionsprotokolle zu schreiben. Dieses Skript wird normalerweise von einem Oracle-Systemadministrator geprüft und ausgeführt.  
  
2.  Wenn Sie die ergänzenden Protokollierungsskripts ausführen, wird das Dialogfeld Oracle Credentials for Running Script geöffnet, in dem Sie einen gültigen Oracle-Benutzernamen und das dazugehörige Kennwort angeben können. Informationen zum Bereitstellen der richtigen Oracle-Anmeldeinformationen finden Sie unter [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).  
  
 Bei Bedarf können Sie die Skripts mithilfe von SQL*Plus auch manuell ausführen.  
  
### <a name="to-run-the-scripts-manually"></a>So führen Sie Skripts manuell aus  
  
1.  Klicken Sie auf **Kopieren** , um das Skript in die Zwischenablage einzufügen. Öffnen Sie SQL*Plus, und greifen Sie auf das Verzeichnis mit der Oracle-Quelldatenbank zu. Fügen Sie das Skript in SQL\*Plus ein, um es auszuführen.  
  
### <a name="to-save-the-supplemental-logging-script-in-a-text-file"></a>So speichern Sie das ergänzende Protokollierungsskript in einer Textdatei  
  
1.  Klicken Sie auf **Speichern unter** , und greifen Sie auf den Speicherort zu, an dem Sie die Datei speichern möchten.  
  
2.  Geben Sie der Datei einen Namen, und klicken Sie auf **Speichern** , um die Datei zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bearbeiten der CDC-Instanzeigenschaften](how-to-edit-the-cdc-instance-properties.md)   
 [Oracle-Anmeldeinformationen zum Ausführen von Skripts](oracle-credentials-for-running-script.md)  
  
  

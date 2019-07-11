---
title: Problembehandlung bei Absturz oder Einfrieren von SQL Server Management Studio (SSMS)
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: ''
ms.date: 07/01/2019
ms.openlocfilehash: 424b0863da9d0d2cfb56676bed5c368efc4d9349
ms.sourcegitcommit: 0b0f5aba602732834c8439c192d95921149ab4c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67501187"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Abrufen von Diagnosedaten nach einem SQL Server Management Studio-Absturz (SSMS)

[!INCLUDE[Gilt für](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)

## <a name="get-full-memory-dump-of-sql-server-management-studio-ssms-when-it-hangs-or-crashes"></a>Abrufen eines vollständigen Speicherabbilds von SQL Server Management Studio (SSMS) nach Absturz oder Einfrieren

Führen Sie die folgenden Schritte aus, um Diagnoseinformationen für die Problembehandlung zu erfassen, nachdem SSMS abgestürzt ist oder nicht mehr reagiert.

1. Laden Sie [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) herunter.

2. Entpacken Sie den Download in einen Ordner.

3. Öffnen Sie eine Eingabeaufforderung, und führen Sie den folgenden Befehl aus.

    ```command prompt  <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    If it prompts you to accept a license agreement, select *Agree*.

4. Start SSMS, if it hasn't started already.

5. Reproduce the issue.

6. The text should appear in the cmd prompt about writing the dump file, wait for that to finish.

7. Create a new folder and copy the *.dmp file that is written out to that folder.

8. Copy the following files into the same folder.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Zip up the folder

## Get full memory dump of SSMS when it throws an OutOfMemoryException

You can get a full memory dump with any managed exception.

To capture diagnostic information to troubleshoot an OutOfMemoryException from SSMS, follow the steps below.

1. Download [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Unzip the download into a folder.

3. Open Command Prompt and run the following command.

    ```command prompt
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    Falls Sie aufgefordert werden, einem Lizenzvertrag zuzustimmen, klicken Sie auf *Zustimmen*.

4. Starten Sie SQL Server Management Studio, wenn nicht schon geschehen.

5. Reproduzieren Sie das Problem.

6. In der Eingabeaufforderung sollte Text über das Schreiben der Abbilddatei angezeigt werden. Warten Sie bis dieser Vorgang abgeschlossen ist.

7. Erstellen Sie einen neuen Ordner, und kopieren Sie die geschriebene DMP-Ausgabedatei in diesen Ordner.

8. Kopieren Sie die folgenden Dateien in denselben Ordner.

    „C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll“ „C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll“  „C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll“

9. Komprimieren Sie den Ordner in eine ZIP-Datei.
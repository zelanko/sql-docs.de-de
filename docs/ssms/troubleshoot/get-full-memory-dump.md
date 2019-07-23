---
title: Abrufen eines vollständigen Speicherabbilds zur Problembehandlung von SQL Server Management Studio (SSMS)
Description: Problembehandlung bei aufgehängtem oder abgestürztem SSMS durch Erfassen eines vollständiges Speicherabbilds
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.reviewer: dineth, sstein
ms.custom: ''
ms.date: 05/17/2019
ms.openlocfilehash: 95beb87d72295f4f5ea10b5bb33476d4d27af628
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266724"
---
# <a name="get-full-memory-dump"></a>Erhalten eines vollständigen Speicherabbilds

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

In diesem Artikel erfahren Sie, wie Sie Diagnoseinformationen erfassen, um eine Problembehandlung für ein abgestürztes oder aufgehängtes SQL Server Management Studio (SSMS) vorzunehmen.

Führen Sie zum Erfassen von Diagnoseinformationen für die Problembehandlung die folgenden Schritte aus.

1. Laden Sie [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) herunter.

2. Entpacken Sie den Download in einen Ordner.

3. Öffnen Sie eine Eingabeaufforderung (wie `cmd.exe`), und führen Sie den folgenden Befehl aus:

    ```
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    Sie sollten aufgefordert werden, einem Lizenzvertrag zuzustimmen. Wählen Sie also **Stimme zu** aus.

4. Starten Sie SQL Server Management Studio (SSMS), wenn nicht schon geschehen.

5. Reproduzieren Sie Ihr Problem.

6. In der Eingabeaufforderung sollte Text über das Schreiben der Abbilddatei angezeigt werden. Warten Sie bis dieser Vorgang abgeschlossen ist.

7. Erstellen Sie einen neuen Ordner, und kopieren Sie die geschriebene DMP-Ausgabedatei in diesen Ordner.

8. Kopieren Sie die folgenden Dateien in denselben Ordner.

    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"
    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"
    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Komprimieren Sie den Ordner in eine ZIP-Datei.

## <a name="outofmemoryexception"></a>OutOfMemoryException

Sie können das vollständige Speicherabbild von SSMS auch abrufen, wenn eine „OutOfMemoryException“ ausgelöst wird (es kann sich um jede verwaltete Ausnahme handeln).

Führen Sie zum Erfassen von Diagnoseinformationen für die Problembehandlung einer „OutOfMemoryException“-Ausnahme in SSMS die folgenden Schritte aus.

1. Laden Sie [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) herunter.

2. Entpacken Sie den Download in einen Ordner.

3. Öffnen Sie eine Eingabeaufforderung, und führen Sie den folgenden Befehl aus.

    ```cmd
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    Sie sollten aufgefordert werden, einem Lizenzvertrag zuzustimmen. Wählen Sie also **Stimme zu** aus.

4. Starten Sie SQL Server Management Studio, wenn nicht schon geschehen.

5. Reproduzieren Sie das Problem.

6. In der Eingabeaufforderung sollte Text über das Schreiben der Abbilddatei angezeigt werden. Warten Sie bis dieser Vorgang abgeschlossen ist.

7. Erstellen Sie einen neuen Ordner, und kopieren Sie die geschriebene DMP-Ausgabedatei in diesen Ordner.

8. Kopieren Sie die folgenden Dateien in denselben Ordner.

    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"
    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"
    * "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Komprimieren Sie den Ordner in eine ZIP-Datei.

## <a name="share-the-information"></a>Freigeben der Informationen

1. Zum Freigeben der Informationen für das SSMS-Team protokollieren Sie das Problem auf https://aka.ms/sqlfeedback.

2. Geben Sie dann die erfasste Speicherabbilddatei auf OneDrive (oder Ähnlichem) frei, von wo die Datei abgerufen werden kann.

    > [!Important]
    > Speicherabbilddateien können vertrauliche Informationen enthalten.

## <a name="next-steps"></a>Nächste Schritte

[SQL Server Management Studio](../sql-server-management-studio-ssms.md)
---
title: Problembehandlung bei Abstürzen von SSMS
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 09/18/2019
ms.openlocfilehash: f994a44d6fe0f458ae8f8d8be0351421322e7967
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75243879"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Abrufen von Diagnosedaten nach einem SQL Server Management Studio-Absturz (SSMS)

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

## <a name="get-full-memory-dump-after-a-hang-or-crash"></a>Abrufen eines vollständigen Speicherabbilds nach Hängen oder Absturz

Abrufen eines vollständigen Speicherabbilds von SQL Server Management Studio (SSMS) nach Hängen oder Absturz.

Führen Sie die folgenden Schritte aus, um Diagnoseinformationen für die Problembehandlung zu erfassen, nachdem SSMS abgestürzt ist oder nicht mehr reagiert.

1. Laden Sie [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) herunter.

2. Entpacken Sie den Download in einen Ordner.

3. Öffnen Sie eine Eingabeaufforderung, und führen Sie den folgenden Befehl aus.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    Falls Sie aufgefordert werden, einem Lizenzvertrag zuzustimmen, klicken Sie auf *Zustimmen*.

4. Starten Sie SSMS, sofern noch nicht geschehen.

5. Reproduzieren Sie das Problem.

6. In der Eingabeaufforderung sollte Text über das Schreiben der Abbilddatei angezeigt werden. Warten Sie bis dieser Vorgang abgeschlossen ist.

7. Erstellen Sie einen neuen Ordner, und kopieren Sie die geschriebene DMP-Ausgabedatei in diesen Ordner.

8. Kopieren Sie die folgenden Dateien in denselben Ordner.

    „C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll“ „C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll“  „C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll“

9. Komprimieren Sie den Ordner in eine ZIP-Datei.

## <a name="get-full-memory-dump-for-an-outofmemoryexception"></a>Vollständiges Speicherabbild für „OutOfMemoryException“

Rufen Sie ein vollständiges Speicherabbild von SSMS bei einer Ausnahme vom Typ „OutOfMemoryException“ ab.

Sie können bei jeder verwalteten Ausnahme ein vollständiges Speicherabbild abrufen.

Führen Sie zum Erfassen von Diagnoseinformationen für die Problembehandlung einer „OutOfMemoryException“-Ausnahme in SSMS die folgenden Schritte aus:

1. Laden Sie [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) herunter.

2. Entpacken Sie den Download in einen Ordner.

3. Öffnen Sie eine Eingabeaufforderung, und führen Sie den folgenden Befehl aus.

    ```console
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

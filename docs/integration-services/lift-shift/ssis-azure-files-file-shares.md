---
title: Öffnen und Speichern von Dateien mit in Azure bereitgestellten SSIS-Paketen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Dateien lokal und in Azure öffnen und speichern, wenn Sie SSIS-Pakete, die lokale Dateisysteme verwenden, per Lift & Shift in SSIS in Azure migrieren.
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4f9d5e91db382d59dc156ed919c1af06cc56b77
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35410472"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Öffnen und Speichern von Dateien lokal und in Azure mit in Azure bereitgestellten SSIS-Paketen

In diesem Artikel wird beschrieben, wie Sie Dateien lokal und in Azure öffnen und speichern, wenn Sie SSIS-Pakete, die lokale Dateisysteme verwenden, per Lift & Shift in SSIS in Azure migrieren.

> [!IMPORTANT]
> Derzeit unterstützt der SSIS-Katalog (SSISDB) nur einen einzelnen Satz von Anmeldeinformationen. Infolgedessen können Sie nicht verschiedene Sätze von Anmeldeinformationen verwenden, um eine Verbindung mit mehreren lokalen Dateifreigaben und Azure Files-Dateifreigaben herzustellen.

## <a name="save-temporary-files"></a>Speichern von temporären Dateien
Wenn Sie temporäre Dateien während einer einzelnen Paketausführung speichern und verarbeiten müssen, können Pakete das aktuelle Arbeitsverzeichnis (`.`) oder den temporären Ordner (`%TEMP%`) Ihrer Azure SSIS Integration Runtime-Knoten verwenden.

## <a name="use-on-premises-file-shares"></a>Verwenden von lokalen Dateifreigaben
Wenn Sie Pakete, die lokale Dateisysteme verwenden, zu SSIS in Azure migrieren und weiterhin **lokale Dateifreigaben** verwenden möchten, führen Sie die folgenden Schritte durch:
1.  Übertragen Sie die Dateien von den lokalen Dateisystemen auf die lokalen Dateifreigaben.
2.  Verknüpfen Sie die lokalen Dateifreigaben mit einem virtuellen Azure-Netzwerk.
3.  Verknüpfen Sie Ihre Azure SSIS IR mit demselben virtuellen Netzwerk. Weitere Informationen finden Sie unter [Verknüpfen einer Azure SSIS Integration Runtime mit einem virtuellen Netzwerk](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Verbinden Sie Ihre Azure SSIS IR mit den lokalen Dateifreigaben innerhalb desselben virtuellen Netzwerks, indem Sie Anmeldeinformationen einrichten, die mit der Windows-Authentifizierung verwendet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung](ssis-azure-connect-with-windows-auth.md).
5.  Ändern Sie lokale Dateipfade in Ihren Paketen in UNC-Pfade, die auf lokale Dateifreigaben verweisen. Ändern Sie z.B. den Pfad `C:\abc.txt` in `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Verwenden von Azure-Dateifreigaben
Wenn Sie Pakete, die lokale Dateisysteme verwenden, zu SSIS in Azure migrieren und **Azure Files**verwenden möchten, führen Sie die folgenden Schritte durch:
1.  Übertragen Sie die Dateien von den lokalen Dateisystemen zu Azure Files. Weitere Informationen finden Sie unter [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Verbinden Sie Azure SSIS IR mit Azure Files, indem Sie Anmeldeinformationen einrichten, die mit der Windows-Authentifizierung verwendet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung](ssis-azure-connect-with-windows-auth.md).
3.  Ändern Sie lokale Dateipfade in Ihren Paketen in UNC-Pfade, die auf Azure Files verweisen. Ändern Sie z.B. den Pfad `C:\abc.txt` in `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.

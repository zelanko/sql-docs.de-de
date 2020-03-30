---
title: Herunterladen des SQL Server PowerShell-Moduls
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: carlrab
ms.custom: ''
ms.date: 01/23/2020
ms.openlocfilehash: 99976a12ae76254da5b50c5467df9d9e42fdbbce
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "76920358"
---
# <a name="install-the-sql-server-powershell-module"></a>Installieren des SQL Server PowerShell-Moduls

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Dieser Artikel enthält Anleitungen zur Installation des PowerShell-Moduls **SqlServer**.

## <a name="powershell-modules-for-sql-server"></a>PowerShell-Module für SQL Server

Es gibt zwei SQL Server PowerShell-Module:

- **SqlServer:** Das SqlServer-Modul enthält neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen. Das Modul enthält ebenso aktualisierte Versionen der Cmdlets in **SQLPS**. Um das SqlServer-Modul herunterzuladen, navigieren Sie zu [SqlServer-Modul im PowerShell-Katalog](https://www.powershellgallery.com/packages/Sqlserver).
- **SQLPS:** Das SQLPS-Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul.

> [!NOTE]
> Die Versionen des **SqlServer**-Moduls im PowerShell-Katalog unterstützen die Versionsverwaltung und erfordern Version 5.0 oder höher von PowerShell.

Hilfethemen finden Sie unter:

- [SqlServer](https://docs.microsoft.com/powershell/module/sqlserver)-Cmdlets.
- [SQLPS](https://docs.microsoft.com/powershell/module/sqlps)-Cmdlets.

## <a name="sql-server-management-studio"></a>SQL Server Management Studio

SQL Server Management Studio (SSMS) installiert ab Version 17.0 keines der beiden PowerShell-Module. Um PowerShell mit SSMS zu verwenden, installieren Sie das **SqlServer**-Modul über den [PowerShell-Katalog](https://www.powershellgallery.com/packages/Sqlserver).

> [!NOTE]
> Mit Version 16.x von SSMS ist eine frühere Version des **SqlServer**-Moduls in SQL Server Management Studio (SSMS) enthalten.

## <a name="azure-data-studio"></a>Azure Data Studio

Azure Data Studio installiert keines der beiden PowerShell-Module. Um PowerShell mit Azure Data Studio zu verwenden, installieren Sie das **SqlServer**-Modul über den [PowerShell-Katalog](https://www.powershellgallery.com/packages/Sqlserver).

Sie können die [PowerShell-Erweiterung](../azure-data-studio/powershell-extension.md) verwenden, die umfassende Unterstützung für den PowerShell-Editor in Azure Data Studio bietet.

## <a name="installing-or-updating-the-sqlserver-module"></a>Installieren oder Aktualisieren des SqlServer-Moduls

Starten Sie eine [PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting)-Sitzung als Administrator, um das **SqlServer**-Modul über den PowerShell-Katalog zu installieren. Im integrierten Terminal starten Sie Azure Data Studio auch als Administrator und führen diese Befehle in einer PowerShell-Sitzung aus.

### <a name="install-the-sqlserver-module"></a>Installieren des SqlServer-Moduls

Führen Sie den folgenden Befehl in der PowerShell-Sitzung aus, um das SqlServer-Modul für alle Benutzer zu installieren:

```powershell
Install-Module -Name SqlServer
```

### <a name="to-view-the-versions-of-the-sqlserver-module-installed"></a>So zeigen Sie die Versionen des installierten SqlServer-Moduls an

Führen Sie den folgenden Befehl aus, um die installierten Versionen des SqlServer-Moduls anzuzeigen.

```powershell
Get-Module SqlServer -ListAvailable
```

### <a name="install-for-the-current-user-rather-than-as-an-administrator"></a>Installieren für den aktuellen Benutzer statt als Administrator

Wenn Sie die PowerShell-Sitzung nicht als Administrator ausführen können, installieren Sie mit folgendem Befehl für den aktuellen Benutzer:

```powershell
Install-Module -Name SqlServer -Scope CurrentUser
```

### <a name="to-overwrite-a-previous-version-of-the-sqlserver-module"></a>So überschreiben Sie eine frühere Version des SqlServer-Moduls

Sie können auch den `Install-Module`-Befehl verwenden, um eine frühere Version zu überschreiben.

```powershell
Install-Module -Name SqlServer -AllowClobber
```

> [!Note]
> PowerShell verwendet immer das neueste installierte Modul.

### <a name="update-the-installed-version-of-the-sqlserver-module"></a>Aktualisieren der installierten Version des SqlServer-Moduls

Wenn aktualisierte Versionen des **SqlServer**-Moduls verfügbar sind, können Sie die neuere Version mit folgendem Befehl installieren:

```powershell
Install-Module -Name SqlServer -AllowClobber
```

Sie können den `Update-Module`-Befehl verwenden, um die neueste Version des SQLServer PowerShell-Moduls zu installieren, aber damit werden keine älteren Versionen entfernt. Er installiert die neuere Version parallel, um Ihnen die Möglichkeit zu geben, mit der aktuellen Version zu experimentieren, aber dennoch die älteren Module zur Verfügung zu haben.

Wenn Sie jedoch keine älteren Modulversionen beibehalten möchten, können Sie den `Uninstall-Module`-Befehl verwenden, um vorherige Versionen zu entfernen.

Mit dem folgenden Befehl können Sie mehrere installierte Versionen auflisten:

```powershell
Get-Module SqlServer -ListAvailable
```

Sie können den folgenden Befehl zum Entfernen älterer Versionen verwenden:

```powershell
Uninstall-module -Name SQLServer -RequiredVersion "<version number>" -AllowClobber
```

### <a name="troubleshooting"></a>Problembehandlung

Wenn bei der Installation Probleme auftreten, finden Sie weitere Informationen unter [Install-Module documentation (Dokumentation zu „Install-Module“)](https://www.powershellgallery.com/packages/PowerShellGet/2.2.1) und [Install-Module reference (Referenz zu „Install-Module“)](https://docs.microsoft.com/powershell/module/powershellget/Install-Module).

## <a name="using-a-specific-version-of-the-sqlserver-module"></a>Verwenden einer spezifischen Version des SqlServer-Moduls

Wenn Sie eine spezifische Version des Moduls verwenden möchten, importieren Sie sie mit einer spezifischen Versionsnummer entsprechend mit dem folgenden Befehl:

```powershell
Import-Module SqlServer -Version 21.1.18080
```

## <a name="pre-release-versions-of-the-sqlserver-module"></a>Vorabversionen des SqlServer-Moduls

Vorabversionen (oder „Preview“-Versionen) des SqlServer-Moduls sind möglicherweise im PowerShell-Katalog verfügbar.

> [!IMPORTANT]
> Diese Versionen können über die aktualisierten Cmdlets *Find-Module* und *Install-Module*, die Teil des [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet)-Moduls sind, ermittelt und installiert werden, indem der *-AllowPrerelease*-Switch übergeben wird. Um diese Cmdlets zu verwenden, installieren Sie das PowerShellGet-Modul, und öffnen Sie dann eine neue Sitzung.

### <a name="to-discover-pre-release-versions-of-the-sqlserver-module"></a>So ermitteln Sie Vorabversionen des SqlServer-Moduls

Sie können den folgenden Befehl ausführen, um die Vorabversion bzw. Preview-Version des SqlServer-Moduls zu ermitteln:

```powershell
Find-Module SqlServer -AllowPrerelease
```

### <a name="to-install-a-specific-pre-release-version-of-the-sqlserver-module"></a>So installieren Sie eine bestimmte Vorabversion des SqlServer-Moduls

Wenn Sie eine bestimmte Vorabversion des Moduls installieren möchten, installieren Sie diese mit einer bestimmten Versionsnummer.

Sie können versuchen, den folgenden Befehl zu verwenden:

```powershell
Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease
```

## <a name="sql-server-powershell-on-linux"></a>SQL Server PowerShell unter Linux

Besuchen Sie [Verwalten von SQL Server für Linux mit PowerShell Core](../linux/sql-server-linux-manage-powershell-core.md), um zu erfahren, wie Sie SQL Server PowerShell unter Linux installieren.

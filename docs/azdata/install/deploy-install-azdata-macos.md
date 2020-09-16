---
title: Installieren von „azdata“ für macOS
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool „azdata“ zum Installieren und Verwalten von Big Data-Clustern für macOS installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6662a5ff7ced4c260e2b1a3fbd1efe5a285cf4a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733868"
---
# <a name="install-azdata-on-macos"></a>Installieren von `azdata` unter macOS

Für die macOS-Plattform können Sie die `azdata-cli` mit dem Homebrew-Paket-Manager installieren. Das CLI-Paket wurde unter folgenden macOS-Versionen getestet: 
* 10.13 High Sierra
* 10.14 Mojave
* 10.15 Catalina

## <a name="install-with-homebrew"></a>Installieren mit Homebrew

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>Die `azdata-cli` weist eine Abhängigkeit von den Homebrew-Paketen `python3`, `freetds`, `unixodbc` und `zeromq` auf und installiert diese. Die `azdata-cli` ist garantiert kompatibel mit der aktuellen Version dieser Abhängigkeiten, die in Homebrew veröffentlicht wurde.

## <a name="verify-install"></a>Überprüfen der Installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Aktualisieren

Aktualisieren Sie Ihre lokalen Repositoryinformationen, und upgraden Sie anschließend das Paket `azdata-cli`.

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>Deinstallieren

Verwenden Sie Homebrew, um das Paket `azdata-cli` zu deinstallieren.

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).
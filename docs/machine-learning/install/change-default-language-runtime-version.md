---
title: Ändern der Standardversion der Runtime der R- oder Python-Programmiersprache
description: Erfahren Sie, wie Sie die von einer SQL-Instanz verwendete Standardversion der R- oder Python-Runtime mithilfe von SQL Server 2017 Machine Learning Services oder SQL Server R Services ändern können.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 08/14/2020
ms.topic: how-to
author: garyericson
ms.author: garye
monikerRange: =sql-server-2016||=sql-server-2017||=sqlallproducts-allversions
ms.openlocfilehash: 457d728bd0e4abb5c2cf70063c0330924104c482
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869979"
---
# <a name="change-the-default-r-or-python-language-runtime-version"></a>Ändern der Standardversion der Runtime der R- oder Python-Programmiersprache

[!INCLUDE[SQL Server 2016 and 2017 only](../../includes/applies-to-version/sqlserver2016-2017-only.md)]

In diesem Artikel wird beschrieben, wie Sie die Standardversion von R oder Python ändern können, die in [SQL Server 2016 R Services](../r/sql-server-r-services.md) oder [SQL Server 2017 Machine Learning Services](../sql-server-machine-learning-services.md) verwendet wird.

Im Folgenden sind die Versionen der R- und Python-Runtime aufgeführt, die in den verschiedenen SQL Server-Versionen enthalten sind.

| SQL Server-Version | Dienst | Kumulatives Update | Versionen der R-Runtime | Version der Python-Runtime |
|-|-|-|-|-|
| SQL Server 2016 | R Services | RTM – SP2 CU13 | 3.2.2 | Nicht verfügbar |
| SQL Server 2016 | R Services | SP2 CU14 und höher | 3.2.2 und 3.5.2 | Nicht verfügbar |
| SQL Server 2017 | Machine Learning Services | RTM – CU21 | 3.3.3 | 3.5.2 |
| SQL Server 2017 | Machine Learning Services | CU22 und höher | 3.3.3 und 3.5.2 | 3.5.2 und 3.7.2 |

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen ein kumulatives Update (CU) installieren, um die Standardversion der R- oder Python-Runtime zu ändern:

- **SQL Server 2016:** Kumulatives Update (CU) 14 oder höher für das Services Pack (SP) 2
- **SQL Server 2017:** Kumulatives Update (CU) 22 oder höher

Informationen zum Herunterladen des aktuellen kumulativen Updates finden Sie in den [Neueste Updates für Microsoft SQL Server](../../database-engine/install-windows/latest-updates-for-microsoft-sql-server.md).

> [!NOTE]
> Wenn Sie eine Slipstreaminstallation für das kumulative Update bei einer Neuinstallation von SQL Server durchführen, werden nur die neuesten Versionen der R- und Python-Runtime installiert.

## <a name="change-r-runtime-version"></a>Ändern der Version der R-Runtime

Wenn Sie eines der oben genannten kumulativen Updates für SQL Server 2016 oder 2017 installiert haben, verfügen Sie möglicherweise über mehrere Versionen von R in einer SQL-Instanz. Jede Version ist in einem Unterordner des Instanzordners namens `R_SERVICES.`*&lt;Hauptversion&gt;* . *&lt;Nebenversion&gt;* enthalten (der Ordner aus der ursprünglichen Installation darf keine Versionsnummer an den Ordnernamen anfügen).

Wenn Sie ein kumulatives Update mit R 3.5 installieren, ist der neue Ordner `R_SERVICES`:

- SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.<INSTANCE_NAME>\R_SERVICES.3.5`
- SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.<INSTANCE_NAME>\R_SERVICES.3.5`

Jede SQL-Instanz verwendet eine dieser Versionen als Standardversion von R. Sie können die Standardversion mithilfe des Befehlszeilen-Hilfsprogramms **RegisterRext.exe** ändern. Das Hilfsprogramm befindet sich in jeder SQL-Instanz unter dem R-Ordner:

*&lt;SQL-Instanzpfad&gt;* \R_SERVICES.n.n\library\RevoScaleR\rxLibs\x64\RegisterRext.exe

> [!Note]
> Die in diesem Artikel beschriebene Funktionalität ist nur mit der in kumulativen SQL-Updates enthaltenen Kopie von **RegisterRext.exe** verfügbar. Verwenden Sie nicht die Kopie, die mit der ursprünglichen SQL-Installation bereitgestellt wurde.

Übergeben Sie zum Ändern der Version der R-Runtime die folgenden Befehlszeilenargumente an **RegisterRext.exe**:

- `/configure` – Erforderlich und gibt an, dass Sie die R-Standardversion konfigurieren.

- `/instance:`*&lt;Instanzname&gt;* – Optional. Dies ist die zu konfigurierende Instanz. Wenn nicht angegeben, wird die Standardinstanz konfiguriert.

- `/rhome:`*&lt;Pfad zum Ordner R_SERVICES[n.n]&gt;* – Optional. Der Pfad zum Ordner der Runtimeversion, den Sie als R-Standardversion festlegen möchten.

  Wenn Sie „/rhome“ nicht angeben, ist der konfigurierte Pfad der Pfad, unter dem sich **RegisterRext.exe** befindet.

### <a name="examples"></a>Beispiele

Nachfolgend finden Sie Beispiele für die Änderung der Version der R-Runtime in SQL Server 2016 und 2017.

#### <a name="change-r-runtime-version-in-sql-server-2016"></a>Ändern der Version der R-Runtime in SQL Server 2016

So konfigurieren Sie z. B. **R 3.5** als Standardversion von R für die Instanz MSSQLSERVER01 unter SQL Server 2016

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES.3.5\library\RevoScaleR\rxLibs\x64"

.\RegisterRext.exe /configure /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES.3.5" /instance:MSSQLSERVER01
```

#### <a name="change-r-runtime-version-in-sql-server-2017"></a>Ändern der Version der R-Runtime in SQL Server 2017

So konfigurieren Sie z. B. **R 3.5** als Standardversion von R für die Instanz MSSQLSERVER01 unter SQL Server 2017

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\R_SERVICES.3.5\library\RevoScaleR\rxLibs\x64"

.\RegisterRext.exe /configure /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\R_SERVICES.3.5" /instance:MSSQLSERVER01
```

In diesen Beispielen müssen Sie das Argument `/rhome` nicht angeben, da Sie denselben Ordner angeben, in dem sich **RegisterRext.exe** befindet.

## <a name="change-python-runtime-version"></a>Ändern der Version der Python-Runtime

Wenn Sie CU22 oder höher für SQL Server 2017 installiert haben, verfügen Sie möglicherweise über mehrere Versionen von Python in einer SQL-Instanz. Jede Version ist in einem Unterordner des Instanzordners namens `PYTHON_SERVICES.`*&lt;Hauptversion&gt;* . *&lt;Nebenversion&gt;* enthalten (der Ordner aus der ursprünglichen Installation darf keine Versionsnummer an den Ordnernamen anfügen).

Wenn Sie z. B. ein kumulatives Update mit Python 3.7 installieren, wird ein neuer Ordner `PYTHON_SERVICES` erstellt:

`C:\Program Files\Microsoft SQL Server\MSSQL14.<INSTANCE_NAME>\PYTHON_SERVICES.3.7`  

Jede SQL-Instanz verwendet eine dieser Versionen als Standardversion von Python. Sie können die Standardversion mithilfe des Befehlszeilen-Hilfsprogramms **RegisterRext.exe** ändern. Das Hilfsprogramm befindet sich in jeder SQL-Instanz unter den Python-Ordnern:

*&lt;SQL-Instanzpfad&gt;* `\PYTHON_SERVICES.n.n\Lib\site-packages\revoscalepy\rxLibs\RegisterRExt.exe`

> [!Note]
> Die in diesem Artikel beschriebene Funktionalität ist nur mit der in kumulativen SQL-Updates enthaltenen Kopie von **RegisterRext.exe** verfügbar. Verwenden Sie nicht die Kopie, die mit der ursprünglichen SQL-Installation bereitgestellt wurde.

Übergeben Sie zum Ändern der Version der Python-Runtime die folgenden Befehlszeilenargumente an **RegisterRext.exe**:

- `/configure` – Erforderlich und gibt an, dass Sie die Python-Standardversion konfigurieren.

- `/python` – Gibt an, dass Sie die Python-Standardversion konfigurieren. Optional, wenn Sie `/pythonhome` angeben.

- `/instance:`*&lt;Instanzname&gt;* – Optional. Dies ist die zu konfigurierende Instanz. Wenn nicht angegeben, wird die Standardinstanz konfiguriert.

- `/pythonhome:`*&lt;Pfad zum Ordner PYTHON_SERVICES[n.n]&gt;* – Optional. Der Pfad zum Ordner der Runtimeversion, den Sie als Python-Standardversion festlegen möchten.

  Wenn Sie „/pythonhome“ nicht angeben, ist der konfigurierte Pfad der Pfad, unter dem sich **RegisterRext.exe** befindet.

### <a name="example"></a>Beispiel

So konfigurieren Sie z. B. **Python 3.7** als Standardversion von Python für die Instanz MSSQLSERVER01 unter SQL Server 2017

```cmd
cd "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\PYTHON_SERVICES.3.7\Lib\site-packages\revoscalepy\rxLibs"

.\RegisterRext.exe /configure /pythonhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES.3.7" /instance:MSSQLSERVER01
```

In diesem Beispiel müssen Sie das Argument `/pythonhome` nicht angeben, da Sie denselben Ordner angeben, in dem sich **RegisterRext.exe** befindet.

## <a name="remove-a-runtime-version"></a>Entfernen einer Runtimeversion

Um eine Version von R oder Python zu entfernen, verwenden Sie **RegisterRext.exe** mit dem `/cleanup`-Befehlszeilenargument, wobei Sie dieselben `/rhome`-, `/pythonhome`- und `/instance`-Argumente verwenden, die zuvor beschrieben wurden.

Wenn Sie z. B. den Ordner **R 3.2** aus der Instanz MSSQLSERVER01 entfernen möchten:

```cmd
.\RegisterRext.exe /cleanup /rhome:"C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER01\R_SERVICES" /instance:MSSQLSERVER01
```

Wenn Sie z. B. den Ordner **Python 3.7** aus der Instanz MSSQLSERVER01 entfernen möchten:

```cmd
.\RegisterRExt.exe /cleanup /python /pythonhome:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER01\PYTHON_SERVICES.3.7" /instance:MSSQLSERVER01
```

**RegisterRext.exe** fordert Sie auf, die Bereinigung der angegebenen R-Runtime zu bestätigen:

> *Sind Sie sicher, dass Sie die angegebene Runtime zusammen mit allen darauf installierten Paketen dauerhaft löschen möchten? \[Ja(J)/Nein(N)/Standard(Ja)\]:*

Um zu bestätigen, antworten Sie mit `Y`, oder drücken Sie die EINGABETASTE. Alternativ können Sie diese Aufforderung überspringen, indem Sie `/y` oder `/Yes` mit der Option `/cleanup` eingeben.

> [!NOTE]
> Sie können eine Version nur entfernen, wenn sie nicht als Standard konfiguriert ist und derzeit nicht zum Ausführen von **RegisterRext.exe** verwendet wird.

## <a name="next-steps"></a>Nächste Schritte

- [Abrufen von R-Paketinformationen](../package-management/r-package-information.md)
- [Abrufen von Paketinformationen für Python](../package-management/python-package-information.md)
- [Installieren von Paketen mit R-Tools](../package-management/install-r-packages-standard-tools.md)
- [Installieren von Paketen mit Python-Tools](../package-management/install-python-packages-standard-tools.md)

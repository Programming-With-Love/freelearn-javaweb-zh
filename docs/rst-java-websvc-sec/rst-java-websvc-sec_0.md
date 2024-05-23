# 前言

使用 Web 服务在计算机系统开发中的固有优势与需要对其进行安全管理的原因是相同的。今天，我们可以说没有一家公司能够完全孤立地工作，而不需要与他人互动、共享和消费信息。此外，这也是任何公司最重要的资产。因此，这些要求在代码行之间也是共同的。本书提供了适用解决方案的真实场景，引导您一路前行，以便您可以轻松学习解决可能出现的最常见需求的解决方案和实施。

RESTful Web 服务相对于基于 SOAP 的服务提供了几个优势。例如，在处理数据类型时，根据您用于创建它们的编程语言或库，使用空值（""）而不是 NULL 时可能会出现不一致。此外，当使用不同版本的库来创建/消费 Web 服务时，可能会在映射复杂对象和文件传输的兼容性问题上遇到困难。在某些情况下，即使从.NET 应用程序中使用 Java 创建的 Web 服务，最终也会在两者之间创建一个在 Java 中实现的服务。这种情况在 RESTful Web 服务中不会发生，因为在这种情况下，功能是通过 HTTP 方法调用公开的。

为了保护信息，安全领域有许多功能可以帮助实现这一目标。例如，了解一些问题，比如身份验证和授权如何协助实现所选机制的实施，其中主要目标是使我们的应用程序更安全，更可靠，是至关重要的。选择每种不同的方式来保护应用程序都与您想要解决的问题相关；为此，我们展示了每种方式的使用场景。

我们经常看到大型组织花费时间和精力来创建自己的实现来处理安全性，而不是使用已经解决了我们需要的标准。通过我们想要与您分享的知识，我们希望避免这种重新发明轮子的过程。

# 本书涵盖的内容

第一章，“设置环境”，帮助我们创建我们的第一个功能应用程序，类似于“Hello World”示例，但具有更多功能，并且非常接近现实世界。本章的主要目的是让我们熟悉我们将要使用的工具。

第二章，“保护 Web 服务的重要性”，介绍了 Java 平台中所有可能的身份验证模型。为了让您更好地理解，我们将一步一步地深入探讨如何利用每个可用的身份验证模型。我们将向您展示信息是如何暴露的，以及如何被第三方拦截，并且我们将使用 Wireshark 进行演示，这是一个非常好的工具来解释它。

最后，在本章中，我们将回顾身份验证和授权之间的区别。这两个概念都非常重要，在安全术语的背景下绝对不可能被忽视。

第三章，“使用 RESTEasy 进行安全管理”，展示了 RESTEasy 如何提供处理安全性的机制，从一个相当基本的模型（粗粒度）开始，到一个更精细的模型（细粒度），在这个模型中，您可以进行更彻底的控制，包括管理不仅配置文件，还有编程文件。

第四章，“RESTEasy Skeleton Key”，帮助我们研究 OAuth 实现以及令牌承载者实现和单点登录。所有这些都是为了限制资源共享的方式。与往常一样，您将亲自动手编写代码并进行真实示例。我们想向您展示，通过这些技术在应用程序之间共享资源和信息已经成为最有用和强大的技术之一，使客户或用户只需使用其凭据一次即可访问多个服务，限制第三方应用程序对您的信息或数据的访问，并通过令牌承载者实施访问控制。您将学会应用这些技术和概念，以构建安全灵活的应用程序。

第五章，“数字签名和消息加密”，帮助我们理解使用简单示例的数字签名的好处；您将注意到消息接收者如何验证发送者的身份。此外，我们将模拟外部代理在传输过程中修改数据，并查看数字签名如何帮助我们检测到它，以避免使用损坏的数据。

最后，我们将解释 SMIME 用于主体加密的工作原理，并通过一个示例来加密请求和响应，以便更好地理解。

# 你需要为这本书做什么

为了在本书中实施和测试所有示例，我们将使用许多免费工具，例如以下工具：

+   Eclipse IDE（或任何其他 Java IDE）

+   JBoss AS 7

+   Maven

+   Wireshark

+   SoapUI

# 这本书适合谁

这本书适用于开发人员、软件分析师、架构师或从事软件开发和 RESTful Web 服务的人员。这本书需要一些关于 Java 或其他语言中面向对象编程概念的先前知识。

不需要先前的安全模型知识，因为我们在本书中解释了理论并在实际示例中应用。

# 约定

在本书中，您将找到一些文本样式，用于区分不同类型的信息。以下是这些样式的一些示例，以及它们的含义解释。

文本中的代码词、数据库表名、文件夹名、文件名、文件扩展名、路径名、虚拟 URL、用户输入和 Twitter 句柄显示如下：“我们将修改`web.xml`文件。”

代码块设置如下：

```java
private boolean isUserAllowed(final String username, final String password, final Set<String> rolesSet) {
    boolean isAllowed = false;
    if (rolesSet.contains(ADMIN)) {
      isAllowed = true;
    }
    return isAllowed;
  }
}
```

当我们希望引起您对代码块的特定部分的注意时，相关行或项目将以粗体显示：

```java
final List<String> authorizationList = headersMap.get(AUTHORIZATION_PROPERTY);

```

任何命令行输入或输出都将以以下方式编写：

```java
mvn clean install

```

**新术语**和**重要**单词以粗体显示。您在屏幕上看到的单词，例如菜单或对话框中的单词，会以这种方式出现在文本中：“从弹出窗口中，选择**SSL 设置**选项卡。”

### 注意

警告或重要说明会出现在这样的框中。

### 提示

提示和技巧会以这种方式出现。
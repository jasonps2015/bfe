# BFE

[![GitHub](https://img.shields.io/github/license/baidu/bfe)](https://github.com/baidu/bfe/blob/develop/LICENSE)
[![Travis (.com)](https://img.shields.io/travis/com/baidu/bfe)](https://travis-ci.com/baidu/bfe)
[![Go Report Card](https://goreportcard.com/badge/github.com/baidu/bfe)](https://goreportcard.com/report/github.com/baidu/bfe)
[![GoDoc](https://godoc.org/github.com/baidu/bfe?status.svg)](https://godoc.org/github.com/baidu/bfe/bfe_module)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/3209/badge)](https://bestpractices.coreinfrastructure.org/projects/3209)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fbaidu%2Fbfe.svg?type=shield)](https://app.fossa.io/reports/1bd1bae4-31bf-41bf-8865-320eedbd1f85)

BFE is an open-source layer 7 load balancer derived from proprietary Baidu FrontEnd.

## Advantages
- Multiple protocols supported, including HTTP, HTTPS, SPDY, HTTP2, WebSocket, TLS, etc.
- Content based routing, support user-defined routing rule in advanced domain-specific language.
- Support multiple load balancing policies.
- Flexible plugin framework to extend functionality. Based on the framework, developer can add new features rapidly.
- Detailed built-in metrics available for service status monitor.

## Getting Started
- [Build and run](docs/en_us/install.md)

## Running the tests
- See [Build and run](docs/en_us/install.md)

## Documentation
- [Overview](docs/en_us/overview.md)
- [Build and run](docs/en_us/install.md)
- [Concepts](docs/en_us/concept.md)
- [Functionality](docs/en_us/functionality.md)
- [Monitor](docs/en_us/monitor.md)
- [Plugin](docs/en_us/modules.md)
- [Summary](docs/en_us/SUMMARY.md)

## Contributing
- Please create an issue in [issue list](http://github.com/baidu/bfe/issues).
- Contact Committers/Owners for further discussion if needed.
- Following the golang coding standards.
- See the [CONTRIBUTING](CONTRIBUTING.md) file for details

## Authors
- Owners: [Miao Zhang](mailto:zhangmiao02@baidu.com), [Sijie Yang](mailto:yangsijie@baidu.com)
- Committers: [Sijie Yang](mailto:yangsijie@baidu.com)
- Contributors: [CONTRIBUTORS](CONTRIBUTORS.md)

## Discussion
- Issue: https://github.com/baidu/bfe/issues

## Contact
- Email：bfe-osc@baidu.com

## License
BFE is under the Apache 2.0 license. See the [LICENSE](LICENSE) file for details.
















BFE（Baidu Front End，百度统一前端）是百度的统一七层流量转发平台。BFE平台目前已接入百度大部分流量，每日转发请求接近1万亿，峰值QPS超过1000万。在2019年百度春晚红包活动中，BFE平台在超大用户压力、数次流量波峰下平稳运行，保证了春晚红包活动的顺利进行。

作为综合的流量转发平台，BFE平台集成了以下4大功能：

· 流量接入和转发：支持HTTP、HTTPS、HTTP/2、QUIC等多种协议，并支持强大的应用层路由能力

· 流量全局调度：支持由外网流量调度和内网流量调度共同构成的全局流量调度系统

· 安全和防攻击：支持黑名单封禁、精细限流和应用层防火墙（WAF）等多种防攻击能力

· 实时数据分析：支持分钟级的超高维度时序报表

作为BFE平台的核心组件，BFE转发引擎从2012年开始研发，并于2014年使用Go语言完成重构。

由于基于Go语言，和业界普遍使用的Nginx开源软件相比，BFE具有以下优势：

· 研发效率高：Go语言的开发效率远高于C语言（及Lua），在代码的可维护性方面也有巨大优势。

· 系统的安全和稳定性高：Go语言没有C语言固有的缓冲区溢出隐患，规避了大量的稳定性和安全风险；另外对于异常可以捕捉，保证程序在快速迭代上线的情况下也不崩溃。

有理由相信，从长期趋势看，基于更高级编程语言的软件系统会逐步取得竞争的优势。CPU等硬件资源的价格仍会快速下降，而开发人力成本、项目研发风险、系统稳定性/安全性方面会成为更重要的决策考虑。从这方面出发，主要基于C语言的Nginx会逐步衰落，而类似BFE这样的基于更高级编程语言的软件会逐步成为主流。

另外，BFE在设计中，还特别增加了企业级应用场景的考虑：

· 转发场景的直接支持：和Nginx这样从Web Server转型为Proxy的进化路径不同，BFE直接为转发场景设计，从转发模型和转发配置方面更满足转发场景的需求

· 多租户的支持：在云计算的场景下，多租户复用是普遍的需求。在BFE的设计中，内置提供了多租户的支持

· 结构化的配置：BFE的配置设计，大量使用JSON这样的结构化方式，便于和相关配置管理系统对接

· 丰富的监控探针：作为一个工业级软件，在BFE的设计中充分考虑了线上监控的需求，BFE程序通过HTTP方式向外暴露数千个内部状态变量


为了促进负载均衡技术的交流和发展，BFE转发引擎于2019年夏天正式开源。

BFE目前已开源并支持以下重要能力：

1、主流网络协议接入

· 支持HTTP/HTTPS/SPDY/HTTP2/WebSocket等

· 支持TLS/HTTP/ WebSocket反向代理模式

2、可扩展插件框架

· 通过可扩展插件框架，快速定制开发扩展模块，满足业务定制化需求

· 内置重写、重定向、流量修改、封禁等丰富插件

3、基于请求内容的分流

· 基于领域专有语言的分流规则，满足复杂业务场景定制化流量转发

· 支持完备的分流条件原语集，包括基于请求内容（URI/Header/Cookie等）以及请求上下文（IP、协议、标签、时间等）的条件原语。

4、灵活的负载均衡策略

· 支持集群级别负载均衡及实例级别负载均衡，实现多可用区容灾及过载保护

· 内置加权轮询、加权最小连接数策略，基于IP或请求内容识别用户实现会话保持

关于BFE开源版本详情及后续路线图，可登录github直接搜索BFE。

BFE转发引擎的研发过程，秉承了百度优良的研发传统，经过了多年的技术积累。BFE已经在百度稳定运行多年，并历经多次大流量的洗礼。以开源贡献社区，是百度技术价值体现的重要方式。希望能借BFE开源的机会，与各位同行切磋技术，共建网络接入领域的开源技术生态。

BFE的开源技术沙龙将于12月7日下午在北京举办。


— 完 —

相关搜索
nginx配置
nginx反向代理
nginx负载均衡


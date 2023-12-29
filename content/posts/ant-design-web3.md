---
title: ant-design-web3
date: 2023-12-29T12:18:08+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1702891150984-9ebc4e572b1d?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDM4MjMzMzJ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1702891150984-9ebc4e572b1d?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDM4MjMzMzJ8&ixlib=rb-4.0.3
---

# [ant-design/ant-design-web3](https://github.com/ant-design/ant-design-web3)

<div align="center">

<img height="180" src="https://github.com/ant-design/ant-design/assets/507615/12d2c16d-92b1-4202-ba6f-4da5ee3622ba">

<h1 align="center">Ant Design Web3</h1>

A collection of components for Web3.

[![CI status][github-action-image]][github-action-url] [![codecov][codecov-image]][codecov-url] [![NPM version][npm-image]][npm-url] [![NPM downloads][download-image]][download-url]

[![Follow Twitter][twitter-image]][twitter-url] [![antd][antd-image]][antd-url] [![dumi][dumi-image]][dumi-url]

English · [中文](./README-zh_CN.md)

[github-action-image]: https://github.com/ant-design/ant-design-web3/workflows/Test/badge.svg
[github-action-url]: https://github.com/ant-design/ant-design-web3/actions/workflows/test.yml
[codecov-image]: https://img.shields.io/codecov/c/github/ant-design/ant-design-web3/master.svg?style=flat-square
[codecov-url]: https://codecov.io/gh/ant-design/ant-design-web3/branch/master
[npm-image]: https://img.shields.io/npm/v/@ant-design/web3.svg?style=flat-square
[npm-url]: https://npmjs.org/package/@ant-design/web3
[download-image]: https://img.shields.io/npm/dm/@ant-design/web3.svg?style=flat-square
[download-url]: https://npmjs.org/package/@ant-design/web3
[dumi-image]: https://img.shields.io/badge/docs%20by-dumi-blue?style=flat-square
[dumi-url]: https://github.com/umijs/dumi
[antd-image]: https://camo.githubusercontent.com/200800486bf56a3f00be17fd8b81711349ee51cebf9c6e7ff2f67aac3ceb4e62/68747470733a2f2f62616467656e2e6e65742f62616467652f69636f6e2f416e7425323044657369676e3f69636f6e3d68747470733a2f2f67772e616c697061796f626a656374732e636f6d2f7a6f732f616e7466696e63646e2f507034575067564442332f4b4470677667754d704766716148506a6963524b2e737667266c6162656c
[antd-url]: https://ant.design
[twitter-image]: https://img.shields.io/twitter/follow/AntDesignWeb3.svg?label=Ant%20Design%20Web3
[twitter-url]: https://twitter.com/AntDesignWeb3
[bundlephobia-image]: https://badgen.net/bundlephobia/minzip/@ant-design/web3?style=flat-square
[bundlephobia-url]: https://bundlephobia.com/package/@ant-design/web3

</div>

- Home Page: https://web3.ant.design
- Documentation: https://web3.ant.design/guide
- 国内加速官网: https://web3.antdigital.dev

## Features

- 🎨 Ant Design Friendly
- 📦 Out-of-the-Box Experience
- 🔌 Compatibility with Different Chains

## Installation

```shell
npm i antd @ant-design/web3 --save
```

## Usage

```ts
import { Address } from '@ant-design/web3';

export default () => {
  return <Address address="0x1234567890123456789012345678901234567890" />;
};
```

## Development

```shell
pnpm i
pnpm dev
```

## Contributing

<a href="https://github.com/ant-design/ant-design-web3/graphs/contributors" target="_blank">
  <table>
    <tr>
      <th colspan="2">
        <br/>
        <img src="https://contrib.rocks/image?repo=ant-design/ant-design-web3"><br/><br/>
      </th>
    </tr>
    <tr>
      <td>
        <picture>
          <source 
            media="(prefers-color-scheme: dark)" 
            srcset="https://next.ossinsight.io/widgets/official/compose-org-active-contributors/thumbnail.png?activity=active&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=2x3&color_scheme=dark"
          />
          <img 
            alt="Contributors of ant-design/ant-design-web3" 
            src="https://next.ossinsight.io/widgets/official/compose-org-active-contributors/thumbnail.png?activity=active&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=2x3&color_scheme=light"
          />
        </picture>
      </td>
      <td rowspan="2">
        <picture>
          <source 
            media="(prefers-color-scheme: dark)" 
            srcset="https://next.ossinsight.io/widgets/official/compose-org-participants-growth/thumbnail.png?activity=active&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=4x7&color_scheme=dark"
          />
          <img 
            alt="Contributors of ant-design/ant-design-web3" 
            src="https://next.ossinsight.io/widgets/official/compose-org-participants-growth/thumbnail.png?activity=active&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=4x7&color_scheme=light"
          />
        </picture>
      </td>
    </tr>
    <tr>
      <td>
        <picture>
          <source 
            media="(prefers-color-scheme: dark)" 
            srcset="https://next.ossinsight.io/widgets/official/compose-org-active-contributors/thumbnail.png?activity=new&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=2x3&color_scheme=dark"
          />
          <img 
            alt="Contributors of ant-design/ant-design-web3" 
            src="https://next.ossinsight.io/widgets/official/compose-org-active-contributors/thumbnail.png?activity=new&period=past_28_days&owner_id=12101536&repo_ids=680030799&image_size=2x3&color_scheme=light"
          />
        </picture>
      </td>
    </tr>
  </table>
</a>

<!-- Made with [OSS Insight](https://ossinsight.io/) -->

Any type of contribution is welcome, here are some examples of how you may contribute to this project:

- Use Ant Design Web3 in your daily work.
- Submit [issues](https://github.com/ant-design/ant-design-web3/issues) to report bugs or ask questions.
- Join our [discussion](https://github.com/ant-design/ant-design-web3/discussions) and provide us with suggestions.
- Propose [pull requests](https://github.com/ant-design/ant-design-web3/pulls) to improve our code.

To better participate and contribute, please read our [contribution guidelines](https://web3.ant.design/guide/contributing).

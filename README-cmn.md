[粵語](README.md) | [English](README-en.md)

<div lang="cmn">

<h1 align="center">Rime 粵語拼音方案</h1>

<p align="center">
<a href="https://github.com/rime/rime-cantonese/issues"><img src="https://img.shields.io/badge/%E6%AD%A1%E8%BF%8E-%E5%8F%83%E8%88%87%E8%B2%A2%E7%8D%BB-1dd3b0?style=for-the-badge&logo=github"/></a>
<a href="https://github.com/rime/rime-cantonese/releases"><img src="https://img.shields.io/github/v/release/rime/rime-cantonese?color=38618c&label=%E7%A9%A9%E5%AE%9A%E7%99%BC%E4%BD%88%E7%89%88%E6%9C%AC&style=for-the-badge"/></a>
<a href="https://travis-ci.com/github/rime/rime-cantonese"><img src="https://img.shields.io/travis/com/rime/rime-cantonese?label=%E5%B0%81%E8%A3%9D%E7%A8%8B%E5%BC%8F&logo=travis-ci&logoColor=white&style=for-the-badge"/></a>
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://img.shields.io/github/license/rime/rime-cantonese?color=blue&label=%E6%8E%88%E6%AC%8A%E6%A2%9D%E6%AC%BE&logo=creative-commons&logoColor=white&style=for-the-badge"/></a>
</p>

配方：℞ `cantonese`

`jyut6ping3` 是聲調顯示版方案，`jyut6ping3_ipa` 是 IPA 顯示版方案。

**Telegram 用户交流組**：[![t.me/rime_cantonese](https://img.shields.io/badge/rime_cantonese-blue?style=flat-square&logo=telegram)](https://t.me/rime_cantonese)

**Gitter 交流室**：[![Gitter](https://img.shields.io/badge/rime_cantonese-blueviolet?style=flat-square&logo=gitter)](https://gitter.im/rime-cantonese/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

**拼音方案**

- 本方案**僅僅**支援「香港語言學學會粵語拼音方案」（簡稱「**粵拼**」）：
    - [Jyutping 粵拼 | lshk](https://www.lshk.org/jyutping)
    - [粵拼：香港語言學學會粵語拼音方案](https://www.jyutping.org/jyutping/)
    - [香港語言學學會粵語拼音方案](https://zh.wikipedia.org/wiki/香港語言學學會粵語拼音方案)
- 分歧拼音方案補丁：詳情請參閱 [`CanCLID/rime-cantonese-schemes`](https://github.com/CanCLID/rime-cantonese-schemes)。

**演示**

| 粵語拼音                   | 粵語拼音（IPA 版）        |
| -------------------------- | ------------------------- |
| ![聲調版](./demo/tone.gif) | ![IPA 版](./demo/ipa.gif) |

* 分歧拼音方案排版工具：[`CanCLID/rime-cantonese-schemes-editor`](https://github.com/CanCLID/rime-cantonese-schemes-editor)

## 安裝

詳細教程請見[安裝教程](https://github.com/rime/rime-cantonese/releases)。

如有問題，歡迎加入上述 Telegram 交流組尋求協助。

## 使用說明

### 聲調輸入

輸入時可忽略聲調，也可按照下列鍵位輸入：

1. v：陰平，打 `siv` 輸出「詩」；上陰入，打 `sikv` 輸出「色」
2. x：陰上，打 `six` 輸出「史」
3. q：陰去，打 `siq` 輸出「試」；下陰入，打 `sekq` 輸出「錫」
4. vv：陽平，打 `sivv` 輸出「時」
5. xx：陽上，打 `sixx` 輸出「市」
6. qq：陽去，打 `siqq` 輸出「事」；陽入，打 `sikqq` 輸出「食」

### 添加模糊音支援

本方案預設**不支援**任何模糊音或懶音，即區分 n-/l-, &empty;-/ng- 等常見懶音。若要啓用模糊音，先打開 `jyut6ping3.schema.yaml` ，取消 `speller/algebra:` 相應代碼的註釋（刪除前置 `#` 號）。例如想支援 n-/l- 不分，`speller/algebra:` 相應行數應改爲：

```yaml
# 取消下行註釋，支援 n- 併入 l- ，如「你」讀若「理」
- derive/^n(?!g)/l/
```

然後重新部署，試一下打 lei hou，可以看到也能輸出「你好」了。

### 用字標準切換

本方案預設採用 OpenCC 用字標準（選單中顯示為「傳統漢字」）。也支援**香港傳統漢字**、**臺灣傳統漢字**和**大陆简化汉字**。要切換用字標準，請按 <kbd>Ctrl</kbd> + <kbd>`</kbd> 然後在菜單選擇。

### Emoji 輸入

按 <kbd>Ctrl</kbd> + <kbd>`</kbd> 打開菜單，然後點擊 <kbd>2</kbd>，選擇【有 Emoji】，即可啓用 emoji —— 每當你輸入一個中文詞，選字表即會出現相應的 emoji 符號。

emoji 碼表請見[此處](https://github.com/rime/rime-emoji/tree/master/opencc)。

如果想永久啓用 emoji，可以把 `jyut6ping3.schema.yaml` 中的 `switches` 修改爲：

```yaml
- name: emoji_suggestion
  # 取消下行註釋，預設啓動 emoji
  reset: 1
  states: [ 冇 Emoji, 有 Emoji ]
```

### 反查

本方案支援普通話拼音、粵語兩分、筆畫、倉頡反查，反查鍵：

- 普通話拼音：<kbd>`</kbd>
- 粵語兩分：<kbd>r</kbd>
- 筆畫：<kbd>x</kbd>
- 倉頡五代：<kbd>v</kbd>

### 特殊符號輸入

本方案支持特殊符號輸入，輸入方法爲 <kbd>/</kbd> + 符號代碼。

符號代碼請見：

- [`symbols.yaml`](https://github.com/rime/rime-prelude/blob/master/symbols.yaml)
- [`symbols_cantonese.yaml`](symbols_cantonese.yaml)

## 字音及詞庫資料來源

見本倉庫 [Wiki](https://github.com/rime/rime-cantonese/wiki)。

## 貢獻指南

如果有任何修改意見，或希望參與本項目，可以直接[在 issue 分頁中提出](https://github.com/rime/rime-cantonese/issues)，也可以在上述 [Telegram 交流組](https://t.me/rime_cantonese)中直接反饋意見。

---

本項目由「粵語計算語言學基礎建設組」([@CanCLID](https://github.com/CanCLID)) 維護，遵循「[共享創意-署名-4.0國際](http://creativecommons.org/licenses/by/4.0/)」協議發佈。（條文以英文版本爲準）
</div>

This work is maintained by the Cantonese Computational Linguistics Infrastructure Development Workgroup ([@CanCLID](https://github.com/CanCLID)), and released under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
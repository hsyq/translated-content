---
title: AudioBufferSourceNode.buffer
slug: Web/API/AudioBufferSourceNode/buffer
l10n:
  sourceCommit: 02e1bfcad5fd0de845fb033d331c3c027afa2d6e
---

{{ APIRef("Web Audio API") }}

**`buffer`** は {{ domxref("AudioBufferSourceNode") }} インターフェイスのプロパティで、音声データのソースとして {{domxref("AudioBuffer")}} を使用して音声を再生する機能を提供します。

`buffer` プロパティに `null` という値を設定すると、ノードは無音を含む単一のチャンネルを生成します（つまり、すべてのサンプルが 0 になります）。

## 値

ノードが再生する音を表すデータを格納した {{domxref("AudioBuffer")}}。

## 例

> **メモ:** 動作する完全な例は、[このコードをライブ実行](https://mdn.github.io/webaudio-examples/audio-buffer/)または[ソースを閲覧](https://github.com/mdn/webaudio-examples/blob/master/audio-buffer/index.html)してください。

```js
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);

button.onclick = () => {
  // Fill the buffer with white noise;
  //just random values between -1.0 and 1.0
  for (let channel = 0; channel < channels; channel++) {
    // This gives us the actual ArrayBuffer that contains the data
    const nowBuffering = myArrayBuffer.getChannelData(channel);
    for (let i = 0; i < frameCount; i++) {
      // Math.random() is in [0; 1.0]
      // audio needs to be in [-1.0; 1.0]
      nowBuffering[i] = Math.random() * 2 - 1;
    }
  }

  // Get an AudioBufferSourceNode.
  // This is the AudioNode to use when we want to play an AudioBuffer
  const source = audioCtx.createBufferSource();
  // set the buffer in the AudioBufferSourceNode
  source.buffer = myArrayBuffer;
};
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [ウェブ音声 API の使用](/ja/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [ウェブ音声 API](/ja/docs/Web/API/Web_Audio_API)

# three.js

[![NPM Package][npm]][npm-url]
[![Build Size][build-size]][build-size-url]
[![NPM Downloads][npm-downloads]][npmtrends-url]
[![DeepScan][deepscan]][deepscan-url]
[![Discord][discord]][discord-url]

#### JavaScript 3D ライブラリ

本プロジェクトの目的は、使いやすく軽量で、クロスブラウザ対応の汎用3Dライブラリを作成することです。現在のビルドには WebGL レンダラーのみが含まれていますが、WebGPU（実験的）、SVG、および CSS3D レンダラーもアドオンとして利用可能です。

[Examples](https://threejs.org/examples/) &mdash;
[Docs](https://threejs.org/docs/) &mdash;
[Manual](https://threejs.org/manual/) &mdash;
[Wiki](https://github.com/mrdoob/three.js/wiki) &mdash;
[Migrating](https://github.com/mrdoob/three.js/wiki/Migration-Guide) &mdash;
[Questions](https://stackoverflow.com/questions/tagged/three.js) &mdash;
[Forum](https://discourse.threejs.org/) &mdash;
[Discord](https://discord.gg/56GBJwAnUS)

### 使い方

以下のコードは、シーン、カメラ、および立方体（キューブ）を作成し、そのキューブをシーンに追加します。次に、シーンとカメラ用の `WebGL` レンダラーを作成し、そのビューポートを `document.body` 要素に追加します。最後に、シーン内のキューブをカメラに対してアニメーションさせます。

```javascript
import * as THREE from 'three';

const width = window.innerWidth, height = window.innerHeight;

// 初期化

const camera = new THREE.PerspectiveCamera( 70, width / height, 0.01, 10 );
camera.position.z = 1;

const scene = new THREE.Scene();

const geometry = new THREE.BoxGeometry( 0.2, 0.2, 0.2 );
const material = new THREE.MeshNormalMaterial();

const mesh = new THREE.Mesh( geometry, material );
scene.add( mesh );

const renderer = new THREE.WebGLRenderer( { antialias: true } );
renderer.setSize( width, height );
renderer.setAnimationLoop( animate );
document.body.appendChild( renderer.domElement );

// アニメーション

function animate( time ) {

	mesh.rotation.x = time / 2000;
	mesh.rotation.y = time / 1000;

	renderer.render( scene, camera );

}
```

すべてが正しく動作すれば、[こちら](https://jsfiddle.net/v98k6oze/)のように表示されます。

### リポジトリのクローン

すべての履歴を含めてリポジトリをクローンすると、約2GBのダウンロードになります。すべての履歴が必要ない場合は、`depth` パラメーターを使用することでダウンロードサイズを大幅に削減できます。

```sh
git clone --depth=1 https://github.com/mrdoob/three.js.git
```

### 変更履歴

[Releases](https://github.com/mrdoob/three.js/releases)


[npm]: https://img.shields.io/npm/v/three
[npm-url]: https://www.npmjs.com/package/three
[build-size]: https://badgen.net/bundlephobia/minzip/three
[build-size-url]: https://bundlephobia.com/result?p=three
[npm-downloads]: https://img.shields.io/npm/dw/three
[npmtrends-url]: https://www.npmtrends.com/three
[deepscan]: https://deepscan.io/api/teams/16600/projects/19901/branches/525701/badge/grade.svg
[deepscan-url]: https://deepscan.io/dashboard#view=project&tid=16600&pid=19901&bid=525701
[discord]: https://img.shields.io/discord/685241246557667386
[discord-url]: https://discord.gg/56GBJwAnUS

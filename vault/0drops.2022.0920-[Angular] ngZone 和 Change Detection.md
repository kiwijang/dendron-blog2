---
id: 9tqljuuooemk86j20mg6nch
title: '1213 [Angular] ngZone 和 Change Detection'
desc: ''
updated: 1672149805071
created: 1663605777459
tags:
  - PROG.Angular
status: w
---

## 先備知識

ES6 的 class 是一種為了讓 JavaScript 的類別更容易使用的語法糖。這種語法糖提供了一個更直覺和更易於使用的方法來定義物件，允許您使用更簡潔和模塊化的代碼來實現物件導向程式設計。這種語法糖在 ES6 中引入，提供了一種新的方法來定義類別，並允許您定義類別成員，包括屬性和方法。

### 原型鏈

```javascript
function Person(
  firstName,
  lastName
) {
  this.firstName =
    firstName;
  this.lastName =
    lastName;
}

Person.prototype.fullName =
  function () {
    return (
      this
        .firstName +
      " " +
      this
        .lastName
    );
  };
```

### 語法糖

```javascript
class Person {
  constructor(
    firstName,
    lastName
  ) {
    this.firstName =
      firstName;
    this.lastName =
      lastName;
  }

  fullName() {
    return (
      this
        .firstName +
      " " +
      this
        .lastName
    );
  }
}

const person =
  new Person(
    "John",
    "Doe"
  );
console.log(
  person.fullName()
); //
```

使用方法都一樣:

```javascript
const person =
  new Person(
    "John",
    "Doe"
  );
console.log(
  person.fullName()
); // prints "John Doe"
```

### Angular compiler

Angular 的 compiler 是基於 TypeScript 語言實作的，並且使用了一些類似於 AST（抽象語法樹）的技術來分析和處理應用程式的源代碼。在轉換過程中，compiler 會進行語法分析、符號檢查和代碼生成等步驟，最終產生能夠在瀏覽器中執行的 JavaScript 代碼。

TypeScript 是一種由 Microsoft 開發的程式語言，它是 JavaScript 的超集，提供了類型系統和面向對象编程的特性。Angular 的 compiler 可以將 TypeScript 編譯成 JavaScript，讓瀏覽器可以理解和執行。

當 Angular 程式碼被加載到瀏覽器時，Angular 的 compiler 會在背景執行，負責解析模板並生成對應的 JavaScript 代碼。這些代碼會被執行，用來更新網頁內容，以反應使用者的互動。

Angular 的 compiler 是一個非常強大的工具，它可以提供許多有用的功能，如靜態型別檢查、自動化優化、代碼生成等。它的出現大大提高了 Angular 的開發效率和可維護性。

![](/assets/images/2022-12-13-16-21-46.png)

> 在 Angular 中我們可以用裝飾器給 calss 一些 metadata。就是要寫給 compiler 看的。

### Angular Decorator 裝飾器

Angular 裝飾器是一種特殊的語法，可以用來修改程式碼中的類別定義。裝飾器可以添加、修改或刪除類別的某些屬性或方法，並且可以控制類別如何被編譯。

Angular 裝飾器的用途非常廣泛，它可以用來實現許多不同的功能。例如，裝飾器可以用來標記一個類別是一個 Angular 組件，或者標記一個屬性是一個輸入變量，或者標記一個方法是一個事件處理器等。

裝飾器非常方便，可以讓開發人員更快速地定義和使用類別，並且可以讓類別更加結構化和模組化。它是 Angular 的一個重要特性，在 Angular 程式碼中經常被用到。

以下就是 Component 裝飾器的 interface:

https://github1s.com/angular/angular/blob/HEAD/packages/core/src/metadata/directives.ts

```typescript
/**
 * Supplies configuration metadata for an Angular component.
 *
 * @publicApi
 */
export interface Component
  extends Directive {
  /**
   * The change-detection strategy to use for this component.
   *
   * When a component is instantiated, Angular creates a change detector,
   * which is responsible for propagating the component's bindings.
   * The strategy is one of:
   * - `ChangeDetectionStrategy#OnPush` sets the strategy to `CheckOnce` (on demand).
   * - `ChangeDetectionStrategy#Default` sets the strategy to `CheckAlways`.
   */
  changeDetection?: ChangeDetectionStrategy;

  /**
   * Defines the set of injectable objects that are visible to its view DOM children.
   * See [example](#injecting-a-class-with-a-view-provider).
   *
   */
  viewProviders?: Provider[];

  /**
   * The module ID of the module that contains the component.
   * The component must be able to resolve relative URLs for templates and styles.
   * SystemJS exposes the `__moduleName` variable within each module.
   * In CommonJS, this can  be set to `module.id`.
   *
   */
  moduleId?: string;

  /**
   * The relative path or absolute URL of a template file for an Angular component.
   * If provided, do not supply an inline template using `template`.
   *
   */
  templateUrl?: string;

  /**
   * An inline template for an Angular component. If provided,
   * do not supply a template file using `templateUrl`.
   *
   */
  template?: string;

  /**
   * One or more relative paths or absolute URLs for files containing CSS stylesheets to use
   * in this component.
   */
  styleUrls?: string[];

  /**
   * One or more inline CSS stylesheets to use
   * in this component.
   */
  styles?: string[];

  /**
   * One or more animation `trigger()` calls, containing
   * [`state()`](api/animations/state) and `transition()` definitions.
   * See the [Animations guide](/guide/animations) and animations API documentation.
   *
   */
  animations?: any[];

  /**
   * An encapsulation policy for the component's styling.
   * Possible values:
   * - `ViewEncapsulation.Emulated`: Apply modified component styles in order to emulate
   *                                 a native Shadow DOM CSS encapsulation behavior.
   * - `ViewEncapsulation.None`: Apply component styles globally without any sort of encapsulation.
   * - `ViewEncapsulation.ShadowDom`: Use the browser's native Shadow DOM API to encapsulate styles.
   *
   * If not supplied, the value is taken from the `CompilerOptions`
   * which defaults to `ViewEncapsulation.Emulated`.
   *
   * If the policy is `ViewEncapsulation.Emulated` and the component has no
   * {@link Component#styles styles} nor {@link Component#styleUrls styleUrls},
   * the policy is automatically switched to `ViewEncapsulation.None`.
   */
  encapsulation?: ViewEncapsulation;

  /**
   * Overrides the default interpolation start and end delimiters (`{{` and `}}`).
   */
  interpolation?: [
    string,
    string
  ];

  /**
   * A set of components that should be compiled along with
   * this component. For each component listed here,
   * Angular creates a {@link ComponentFactory} and stores it in the
   * {@link ComponentFactoryResolver}.
   * @deprecated Since 9.0.0. With Ivy, this property is no longer necessary.
   */
  entryComponents?: Array<
    | Type<any>
    | any[]
  >;

  /**
   * True to preserve or false to remove potentially superfluous whitespace characters
   * from the compiled template. Whitespace characters are those matching the `\s`
   * character class in JavaScript regular expressions. Default is false, unless
   * overridden in compiler options.
   */
  preserveWhitespaces?: boolean;

  /**
   * Angular components marked as `standalone` do not need to be declared in an NgModule. Such
   * components directly manage their own template dependencies (components, directives, and pipes
   * used in a template) via the imports property.
   *
   * More information about standalone components, directives, and pipes can be found in [this
   * guide](guide/standalone-components).
   */
  standalone?: boolean;

  /**
   * The imports property specifies the standalone component's template dependencies — those
   * directives, components, and pipes that can be used within its template. Standalone components
   * can import other standalone components, directives, and pipes as well as existing NgModules.
   *
   * This property is only available for standalone components - specifying it for components
   * declared in an NgModule generates a compilation error.
   *
   * More information about standalone components, directives, and pipes can be found in [this
   * guide](guide/standalone-components).
   */
  imports?: (
    | Type<any>
    | ReadonlyArray<any>
  )[];

  /**
   * The set of schemas that declare elements to be allowed in a standalone component. Elements and
   * properties that are neither Angular components nor directives must be declared in a schema.
   *
   * This property is only available for standalone components - specifying it for components
   * declared in an NgModule generates a compilation error.
   *
   * More information about standalone components, directives, and pipes can be found in [this
   * guide](guide/standalone-components).
   */
  schemas?: SchemaMetadata[];
}
```

Angular 支援自訂裝飾器，這又是另一個需要探討的主題了。

## Angular 是怎麼更新畫面的?

在 Angular 中，更新畫面主要是通過應用程式的觀察者模式 (observer pattern) 來實現的。具體來說，Angular 會監聽應用程式中的模型變量，當它們發生改變時，Angular 就會更新相應的畫面元素。

在 Angular 中，應用程式的模型變量是存儲在特定的類中的。這些類通常會繼承自 Angular 框架中的一個基礎類，比如 Angular 中的 Component 等類。當這些類中的模型變量發生改變時，Angular 就會根據定義的模板更新畫面。

總的來說，Angular 主要是通過監聽模型變量的變化來更新畫面的，而這些模型變量通常是存儲在特定的類中的。

## ngZone 和 Change Detection

Change Detection 和 ngZone 是 Angular 中的兩個功能，用於處理應用程式中的變化和狀態更新。

Change Detection 是 Angular 的一個核心功能，用於監測應用程式中的變化，並在必要時更新應用程式的使用者界面。它會檢查組件的輸入變數，並在變數更改時進行更新。

ngZone 是 Angular 中的一個服務，用於將代碼放入「觸發網路更新的區域」（zone）中。這有助於檢測代碼執行的更改，並在必要時觸發 Angular 的 Change Detection 過程。這可以幫助應用程式保持最新，並確保使用者界面與應用程式的狀態保持同步。

總的來看，Change Detection 是 Angular 用於監測應用程式中的變化，並在必要時更新使用者界面的功能。而 ngZone 則是一個服務，用於將代碼放入「觸發網路更新的區域」中，以幫助檢測代碼執行的更改，並在必要時觸發 Angular 的 Change Detection 過程。

通常情況下，當你的應用程式中有異步代碼，例如定時器、非同步網路請求或事件監聽器時，你可能會用到「觸發網路更新的區域」。這是因為這些異步代碼可能會在 Angular 的 Change Detection 過程之外執行，並且可能會更改應用程式的狀態。通過使用 ngZone 服務，你可以確保這些異步代碼能夠觸發 Angular 的 Change Detection 過程，使應用程式的狀態保持最新。

Change Detection 是 Angular 中的一個核心功能，用於監測應用程式中的變化，並在必要時更新應用程式的使用者界面。

Change Detection 過程有以下幾個步驟：

- 檢查組件的輸入變數：Angular 會檢查組件的輸入變數，看看有沒有改變。

- 更新組件的輸出值：如果組件的輸入變數有改變，Angular 會更新組件的輸出值。

- 檢查組件的模板：Angular 會檢查組件的模板，看看有沒有使用到輸出值。

- 更新使用者界面：如果組件的模板使用了輸出值，Angular 會更新使用者界面。

在總的來看，Change Detection 過程是一個自動過程，用於監測應用程式中的變化，並在必要時更新使用者界面。

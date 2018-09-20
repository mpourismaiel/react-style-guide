<div dir="rtl">

# شیوه‌نامه‌ی React/JSX از Airbnb

**(Persian Translation of [Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react))**

*یک رویکرد معقول برای React and JSX*

این شیوه‌نامه مبتنی بر استانداردهای موجود در جاوااسکریپت است، هرچند ممکن است برخی از قراردادها (مانند  async/await یا  فیلدهای استاتیک در کلاس) به صورت موردی قابل قبول یا ممنوع باشند. در حال حاضر هر چیزی قبل از مرحله 3 در این راهنما توصیه نمی شود.

</div>

<div dir="rtl">

## فهرست مندرجات

  1. [قوانین اساسی](#قوانین-اساسی)
  1. [تفاوت Class، `React.createClass` و stateless](#تفاوت-class-reactcreateclass-و-stateless)
  1. [Mixinها](#mixinها)
  1. [نام‌گذاری](#نامگذاری)
  1. [تعریف](#تعریف)
  1. [ترازبندی](#ترازبندی)
  1. [Quotes](#quotes)
  1. [فاصله‌گذاری](#فاصله‌گذاری)
  1. [Propها](#propها)
  1. [Refها](#refها)
  1. [پرانتزها](#پرانتزها)
  1. [تگ‌ها](#تگ‌ها)
  1. [توابع](#توابع)
  1. [مرتب‌ سازی](#مرتب‌-سازی)
  1. [`isMounted`](#ismounted)

</div>

<div dir="rtl">

## قوانین اساسی

  - در هر فایل یک کامپوننت ری‌اکت داشته باشید.
    - گرچه, چند [Stateless, یا Pure, Components](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions) در یک فایل امکان پذیر است. eslint: [`react/no-multi-comp`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/no-multi-comp.md#ignorestateless).
  - همیشه از سینتکس JSX استفاده کنید.
  - هیچ‌وقت از `React.createElement` استفاده نکنید مگر آنکه برنامه را از فایلی شروع می‌کنید که JSX نیست.

</div>

<div dir="rtl">

## تفاوت Class، `React.createClass` و stateless

</div>

  - درحالتی که state یا ref یا هر دو را دارید، `class extends React.Component` بهتر از `React.createClass` است.  eslint: [`react/prefer-es6-class`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/prefer-es6-class.md) [`react/prefer-stateless-function`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/prefer-stateless-function.md)

    ```jsx
    // بد
    const Listing = React.createClass({
      // ...
      render() {
        return <div>{this.state.hello}</div>;
      }
    });

    // خوب
    class Listing extends React.Component {
      // ...
      render() {
        return <div>{this.state.hello}</div>;
      }
    }
    ```
    
    و اگر state یا ref ندارید، تابع عادی (نه arrow functions) بهتر از کلاس است: 
    
    ```jsx
    // بد
    class Listing extends React.Component {
      render() {
        return <div>{this.props.hello}</div>;
      }
    }

    // بد (متکی بودن به استنتاج اسم تابع توصیه نمی‌شود) 
    const Listing = ({ hello }) => (
      <div>{hello}</div>
    );

    // خوب
    function Listing({ hello }) {
      return <div>{hello}</div>;
    }
    ```
    
<div dir="rtl">    
    
## Mixinها
    
  - [از mixinها استفاده نکنید](https://facebook.github.io/react/blog/2016/07/13/mixins-considered-harmful.html).
      
  > چرا؟ mixinها وابستگی ضمنی ایجاد می‌کنند، باعث تلاقی اسم‌ها و پیچیدگی گلوله برفی (؟) می‌شن. بیشتر موارد استفاده از mixinها را می‌شود با روش‌های بهتری از طریق کامپونتت‌ها، higher-order کامپوننت‌ها یا ماژول‌های utility انجام داد. 

</div>

<div dir="rtl">

## نام‌گذاری
</div>

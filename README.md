# couponClipperBookmarklet
Automated coupon clipper bookmarklets for popular grocery chains

To conveniently save money, I've created a tool to automate coupon clipping.  It currently works with:

 * <a href="https://www.albertsons.com/foru/coupons-deals.html">Albertsons</a>
 * <a href="https://www.safeway.com/foru/coupons-deals.html">Safeway</a>
 * <a href="https://www.qfc.com/savings/cl/coupons/">QFC</a>
 * <a href="https://www.fredmeyer.com/savings/cl/coupons/">Fred Meyer</a>
 * <a href="https://www.wincofoods.com/coupons/">Winco</a>

Navigate to the desired grocery store coupon page (linked to each above), log in, then click the bookmarklet from your bookmark bar.  You will see live coupons being clipped in-page and a notification with how many coupons have been clipped once completed.

## Installation

 * Copy the following code:
```
javascript:(async function(){const store={albertsons:'.coupon-grid-offers .btn-primary',fredMeyer:'.CouponsDisplayWrapper button.kind-prominent.palette-accent[data-testid^="CouponActionButton-"]',safeway:'.coupon-grid-offers .btn-primary',qfc:'.CouponsDisplayWrapper button.kind-prominent.palette-accent[data-testid^="CouponActionButton-"]',winco:'.coupon-container .coupon__button--clip'};const couponPage=Object.entries(store).find(([name,selector])=>document.querySelector(selector));const couponSelector=couponPage?couponPage[1]:false;let count=0;if(document.querySelectorAll(couponSelector).length){while(document.querySelectorAll(couponSelector).length){const buttons=document.querySelectorAll(couponSelector);if(buttons[0]){buttons[0].click();count++;const delay=Math.random()*(1000-200)+200;await new Promise(resolve=>setTimeout(resolve,delay));}else break;}alert('No more coupons found.  Clipped '+count+' coupons.');}else{alert('No valid coupons found.');}})();
```
 * In most browsers, click the "..." in the top right of the browser
 * "Bookmarks and Lists"
 * "Bookmark Manager"
 * In most browsers, click the "..." in the top right of the bookmark manager
 * "Add new bookmark"
 * Enter the name "Grocery Store Coupon Clipper"
 * In the URL field, paste in the code copied above

## Usage

Navigate to any of the grocery stores linked above.  You will need to log in as normal.  Once logged in on any of the above pages, select the "Grocery Store Coupon Clipper" bookmark and watch as coupons are automatically clipped for you.  When complete, an alert will display showing how many coupons have been clipped.

If no coupons are found (either because they've all be clipped or you're on the wrong page), you'll get an alert that "No valid coupons found."

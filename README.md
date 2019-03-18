_Meeting 18 Maret 2019:_

# _ALI_

## 1. Migrate ChinaBuyBuy -> ALI

- Create new tables in API-2 based on CBB
- Change API calls mechanism
- Modifying Requests-Responses
- Catalogs
- My Products
- Etc.
- Sync ChinaBuyBuy Data
- Commands & Seeders (Cron)
- Webhook calls from ChinaBuyBuy to ALI
- Change API calls mechanism
- Modifying Requests-Responses
- Catalogs
- My Products
- Etc.

## 2. Merge API 1 -> API 2

- Orders
- Users
- Rules
- Global Settings
- Trackings
- Invoices
- Form Validation

## 3. Documentation

- API-2
- API-1

## 4. Frontend Optimization

- Lazy Load
- Invalidate older build
- Form Validation
- Reduce API Calls (caches, includes, etc.)
- Communicate with API Team (edited)

---

# 4. Frontend Optimization:

## Lazy Load:

**- Components yang perlu dibikin lazy load:**

- Pages
- Images
- Tabs (in My Product)
- Cart Details, Order Details (on expand click)

## Invalidate older build:

Mengkonfigurasi webpack supaya saat ke _re-deploy_, cache, cookies and other sttuff doesn't affect the code

## Form Validation:

- **Rule for Prices:**

  - Cannot be empty
  - Must be Number
  - Decimal allowed maximum 2

- **Rules for Regular Text**:

  - Cannot be empty

- **Rule for Number:**
  - Must be Number only
  ***

* **[Catalogs]**

  - Search Product: _Rules for Regular Text_

* **[My Products]**

  - Search Product: _Rules for Regular Text_
  - Description: _Rules for Regular Text_
  - Variant Title: _Rules for Regular Text_
  - Variant Price: _Rule for Prices_
  - Settings Multiplier: _Rule for Prices_
  - Settings Fixed Price: _Rule for Prices_

* **[Carts]**

  - Quantity: _Rule for Number_

* **[Add To Cart]**

  - Quantity: _Rule for Number_

* **[Tracking]**
  - Inputan Tracking Code: _Rule for Regular Text_

## API Calls (includes)

Menginclude kan data data lainnya yang diperlukan sebuah page jadi satu request.

- Di _Page Catalogs_ pada saat fetch data catalog, include-kan:

  - Categories
  - My Products

- Di _Page My Products_ pada saat fetch data my products, include-kan:

  - Rules
  - Categories Owned (buat filter)

- Di _Page Carts_ pada saat fetch data my products, include-kan:
  - Rules

## Vuex Optimization

Mengoptimasi penggunaan vuex. Mungkin beberpaa yang perlu dilakukan:

- Harus ada initial state dan method untuk reset state
- Mutation names harus berupa constants untuk mencegah _typo_ mutation name
- STATE HARUS IMMUTABLE:
  - Selalu _cloneDeep_ data sebelum di ubah
  - Untuk push array jangan pake `.push()` tapi gunakan `.concat()`
- Clear all state saat logout instead of doing refresh

---

### Last but not least...

Always comment your code and make a clear description so that other developers can know what the hell that you did 😈

# Test Plan

## 1. Canonical data

- Same INN cannot create a second company record.
- Company with unconfirmed identity cannot enter КОМПАНИЯ.
- Company without usable general phone cannot enter the main work dataset.
- Source, sphere and script links remain valid.

## 2. Projection integrity

For one canonical company record:

- status ОЧЕРЕДЬ => visible only in the Очередь projection among the four status projections;
- status КЛИЕНТ => visible in КЛИЕНТ;
- status ПЕРЕЗВОНИТЬ => remains outside КЛИЕНТ/АРХИВ and remains available to follow-up workflow;
- status АРХИВ => visible in АРХИВ.

No status change may create a second company record.

## 3. Status actions

Test each status button:

- writes the intended status;
- does not alter unrelated business data;
- moves the record to the correct projection;
- works from record detail on the target mobile app.

## 4. Contact history

- First contact is stored;
- last contact is updated;
- latest comment shown in queue corresponds to the current company record;
- historical contact records remain linked to the same company.

## 5. Orders

- Order links to exactly one company record;
- multiple orders can belong to one company;
- repeat orders do not duplicate the company;
- company card exposes related orders.

## 6. Mobile UX

Verify Android and iOS interface behavior for:

- list opening;
- company drill-down;
- status update buttons;
- linked records;
- compact field layout;
- navigation between the five top-level lists.

Airtable documents mobile support for lists and record details, including update-field buttons and linked-record actions, with some desktop/mobile differences that must be tested explicitly. citeturn108379search1turn108379search4

## 7. Regression

After each schema/interface change rerun:

canonical identity → projection mapping → status buttons → contact history → orders → mobile navigation.

## 8. Release gate

No release until representative-data tests, security/data-safety review and final acceptance evidence are recorded.

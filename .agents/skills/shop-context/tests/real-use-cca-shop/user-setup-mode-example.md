# ShopContext Setup Review

## 1. What I Found

- I found a CCA-style flow from kitting through ship.
- The route includes secondary and primary SMT, touch-up, through-hole install, inspection, test, bonding, conformal coat, UID label, and final inspection.
- Work centers are coded values like `643c01`, `612c04`, `632w01`, `635s01`, `635c01`, and `612w02`.
- The machine list includes SMT, reflow, soldering, AOI, bonding, coating, and microscope equipment.
- The machine list does not include work centers, so machine mappings are inferred and need confirmation.

## 2. What I'm Unsure About

- Whether the broad SMT operations include DEK Horizon, MY300, and IBL VAC 645.
- Whether through-hole install uses Pillarhouse Jade, Solderjet1, manual soldering, or a combination.
- Whether inspection uses AOI, microscopes, or both.
- What equipment supports the Test operation.
- What the coded work centers officially mean.

## 3. Questions For You

1. Do `0300 Process Secondary Side SMT` and `0400 Process Primary Side SMT` both use DEK Horizon, MY300, and IBL VAC 645?
2. Are print/place/reflow tracked separately anywhere else, or only under the broad SMT operations?
3. Does `0600 Install Thru Holes` use Pillarhouse Jade, Solderjet1, manual soldering, or a combination?
4. Does `0800 Insp` use Koh Young Zenith Pro, Mantis Microscopes, both, or another method?
5. What equipment or station supports `0900 Test`?
6. Does `1000 Bonding` use Nordson Dispenser?
7. Does `1100 Conformal Coat` use Conformal Coat Booth?
8. Does `1300 Final Insp` use Mantis Microscopes, Koh Young Zenith Pro, both, or another method?
9. What do these work centers mean: `643c01`, `612c04`, `632w01`, `635s01`, `635c01`, `612w02`?

Optional:
10. Which records are actually retained: AOI results, reflow profiles, test results, bonding records, coating records, final inspection records?

## 4. Next Step

Reply with answers or corrections to the questions above.

I will keep updating the shop reference as you clarify the mappings. I will only generate the full `shop-reference.md` when you ask for the full reference.

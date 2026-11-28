# Glossary

Terms that appear in more than one repository. User-facing documents use the English term and define it
on first use; internal Japanese notes may use the Japanese term.

Which glossary wins ([decision](decisions/2026-11-28-canonical-glossary-and-boundary.md)): this glossary is canonical for
terms used in more than one repository; a repository's own glossary is canonical for terms used only there; a
repository term that uses the same word as a term here must mean the same thing, or be renamed.

| English | 日本語 | Meaning |
|---|---|---|
| Physical-Edge Native Architecture (PENA) | Physical-Edge Native Architecture | The design for computing the physics of a space with the many small, heterogeneous devices placed in it, communicating only with neighbours, while large central models keep doing global reasoning |
| region / patch | 区画 | The part of the space one device computes |
| interface (between regions) | 界面 | The border between two neighbouring regions, where values are exchanged |
| boundary (of the domain) | 境界 | The edge of the region the devices currently compute, including the edges of holes left by devices that have left. Boundary conditions close the computation there. When a PC joins temporarily to forecast, it only helps inside that region; the boundary does not move |
| solver component | 計算部品（アクター） | A physics solver compiled to WebAssembly and run on a device |
| grid solver / learned solver | 格子型アクター／学習型アクター | A classical numerical solver / a trained neural network used as a solver |
| bit-exact | ビット一致 | The split computation produces exactly the same bits as the single-computer computation |
| assimilation (nudging) | データ同化（ナッジング） | Pulling the computed field toward local sensor readings |
| twin | ツイン（デジタルツイン） | The computed state of the real space, kept fitted to reality |
| split control / central control | 分割制御／中央の制御 | One controller per body part exchanging values with neighbours / one policy that sees the whole body |
| numerical error / estimation error | 数値計算の誤差／推定の誤差 | Error between the split and the reference computation / error between the estimate and ground truth. Always say which one is meant |

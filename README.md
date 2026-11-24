# Meningioma Positional Programs — Reproducible Analysis Repository

수막종(meningioma)의 해부학적 위치 프로그램(**척추 *HOX* 메틸화 기울기, 전두개와 *ALX3* 지역화, 1p 결손 용량 효과를 넘어선 *ALX3* 후성유전적 감쇠, 악성 진행에 따른 후기 위치 정체성 붕괴 및 이소성 *HOX* 탈억제의 시간적 선후관계**)을 규명한 논문의 재현성(reproducibility) 코드 및 수치 자료 저장소입니다.

> **Status**: 재현성 파이프라인 스크립트 및 정제 테이블 업로드 준비 중 (Preparing structured code & source-data release). 모든 분석은 공개된 비식별 인체 수막종 및 정상 뇌수막 멀티오믹스 데이터셋만을 사용합니다.

---

## 업로드 예정 구성 (Planned Repository Contents)

| 디렉터리 | 포함 예정 내용 (Planned Contents) |
| :--- | :--- |
| `data/` | 공개 데이터셋 다운로드 스크립트 및 코호트별 환자·종양·검체·절편·다중 오믹스 중복 매니페스트 (`Table S1a,b`; 대용량 원시 IDAT/FASTQ/BAM/RDS 제외) |
| `scripts/01_preprocessing_spinal/` | Raw IDAT `minfi` (`preprocessNoob`) 전처리, 59-SNP 동일인 검증·중복 제거, 척추 *NF2*/22q 수막종(`GSE212449`) 전장 EWAS 및 비선형/hinge 모형 |
| `scripts/02_cranial_discovery_chromatin/` | 두개내 수막종(`GSE189672`/`GSE189521`) 전장 RNA-seq DE·EPIC EWAS, `H3K27ac`/`H3K27me3` ChIP-seq(`GSE85132`, `GSE91372`, `GSE92558`) 및 외부 Yale(`GSE84263`, `GSE91375`) 비모수 검증 |
| `scripts/03_clival_meninges_survival/` | 사대/대후두공 `HOX1–4` 내피세포·공변량 보정 및 29-분할 wild-bootstrap 감사, 태아 뇌수막 참조 아틀라스(`Vinsland et al., 2026`), 정밀 날짜 기반 Cox 무재발생존(RFS) 분석 |
| `scripts/04_anterior_alx3_chr1p_dosage/` | 전방 수막종 내 *ALX3* 감쇠·`MenG C` 농축 분석 및 염색체 1p 완(arm) 유전자 용량 효과 대비 초과 감쇠(beyond-dosage attenuation) 벤치마킹 |
| `scripts/05_snrna_spatial_multiregional/` | 단일핵 전사체(`GSE313693`, `GSE278452`) 신생물-혈관 *HOX* 해리, 10x Visium 공간전사체(39개 고유 종양 / 44개 절편: `GSE313694`, `GSE299374`), 다부위 정위 생검(`GSE151067`, `GSE151921`) ICC |
| `scripts/06_forward_prediction_nested_loocv/` | 척추 레벨 역방향 예측 — 사전 고정 `94-CpG` 선형 모형 및 **엄밀한 fold 내부(`N − 1`) probe QC·16개 모듈 재선택·391,574-CpG 무가설 EWAS nested LOOCV**, 태아→종양 zero-shot 두개내 위치 분류 및 고등급 `posterior-like calls` 교란 감사 |
| `scripts/07_temporal_precedence/` | 악성화 vs 위치 프로그램 붕괴의 선후관계 검증 (`McNemar` 비대칭 포함 검정, 단일핵 병기 진행 캐스케이드, 12쌍 종단 재발 추적, Visium 증식 핫스팟 분석) |
| `scripts/08_verification/` | R–Python 교차 수치 재검산 및 원고·보충표 정합성 자동 검증 스크립트 |
| `results/` | 분석 단계별 요약 통계 CSV 및 통합 보충표 워크북 (`Supplementary_Tables.xlsx`, 54 sheets) |
| `figures/` | Main Figures 1–9 및 Supplementary Figures 1–12 재현 스크립트 (`600 dpi` TIFF/PNG 생성) |
| `env/` | 실행 환경 명세 (`R 4.3.2` / Bioconductor 3.18 및 `Python 3.12+` 패키지 버전 잠금 파일) |

---

## 분석 대상 공개 데이터셋 (Public Datasets Referenced)

- **척추 수막종 DNA 메틸화**: `GSE212449` (Ricklefs et al., *Acta Neuropathol.* 2022)
- **두개내 수막종 1:1 매칭 RNA-seq & EPIC 메틸화**: `GSE189672`, `GSE189521` 및 BCM 임상 테이블 (Bayley et al., *Sci. Adv.* 2022; Patel et al., *PNAS* 2019)
- **외부 다중 오믹스(발현·메틸화·ChIP-seq)**: `GSE84263`, `GSE85132` (Clark et al., *Nat. Genet.* 2016); `GSE91375`, `GSE91372`, `GSE92558` (Harmancı et al., *Nat. Commun.* 2017)
- **정상 발생 뇌수막 단일세포 참조**: `linnarsson-lab/human-meninges-development` (Vinsland et al., *Nat. Cell Biol.* 2026)
- **대규모 Bulk RNA-seq, 성인 경막 scRNA-seq, 정위 다부위 생검 & 이종이식**: `GSE183653`, `GSE183655` (Choudhury et al., *Nat. Genet.* 2022); `GSE151067`, `GSE151921` (Magill et al., *Nat. Commun.* 2020); `GSE224347` (Eaton et al., *Nat. Commun.* 2024)
- **종단 단일핵 전사체(snRNA-seq) & 10x Visium 공간전사체**: `GSE313693` / Zenodo `17941488`, `GSE313694` (Maas et al., *Nat. Genet.* 2026); `GSE278452` (Lee et al., *Nat. Commun.* 2025); `GSE299374` (Aggarwal et al., *Neuro Oncol.* 2026)

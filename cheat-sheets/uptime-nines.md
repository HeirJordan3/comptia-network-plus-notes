# Uptime and the "Nines"

[← Back to index](../README.md)

| Uptime | Nickname | Downtime per year (approx.) |
|---|---|---|
| 99% | two nines | ~3.65 days |
| 99.9% | three nines | ~8.77 hours |
| 99.99% | four nines | ~52.6 minutes |
| 99.999% | five nines | ~5.26 minutes |
| 99.9999% | six nines | ~31.5 seconds |

## How to work it out

Downtime = (100% − uptime%) × minutes in a year

- Minutes in a year: 365 × 24 × 60 = **525,600**
- Five nines: 0.00001 × 525,600 ≈ **5.26 minutes**

## Remember

- Each extra 9 cuts downtime by **10×**
- **Five nines ≈ 5 minutes/year** is the one the exam cares about most
- The uptime target is defined in the **SLA**

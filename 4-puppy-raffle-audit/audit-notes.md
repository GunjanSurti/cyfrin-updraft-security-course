## About

- About the project in my own words 
- `selectWinner` picks the winner, there is a raffle duration 

### High 

- Found a DoS

### Informational 

- `PuppyRaffle::entranceFee` is immutable, and should be like `i_entranceFee`, `ENTRANCE_FEE`. 


----------------------------

- Remember to take notes when ever you found or think anything
- Good design pattern known as `Pull over Push`, where ideally, the user is making a request for funds, instead of a protocol distributing them.

```bash
pandoc report-example.md -o report.pdf --from markdown --template=eisvogel --listings
```
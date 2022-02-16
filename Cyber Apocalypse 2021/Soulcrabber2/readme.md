This one is similar to soulcrabber, except the seed is not hardcoded but equal to the number of second since epoch.
```
SystemTime::now()
        .duration_since(SystemTime::UNIX_EPOCH)
        .expect("Time is broken")
        .as_secs();
```

We can expect the seed is "recent", so we can brute force it, starting from now and decrementing the seed 1 by 1.
We know the input of the flag in "CHTB{", so we can check these correspond to the first 10 values in output.txt:

```
fn test() -> u64 {
    let mut seed = SystemTime::now()
        .duration_since(SystemTime::UNIX_EPOCH)
        .expect("Time is broken")
        .as_secs();
    let mut found = false;
    while !found && seed >=0 {
        let mut rng = StdRng::seed_from_u64(seed);
        let a = format!("{:02x}", ('C' as u8 ^ rng.gen::<u8>()));
        let b = format!("{:02x}", ('H' as u8 ^ rng.gen::<u8>()));
        let c = format!("{:02x}", ('T' as u8 ^ rng.gen::<u8>()));
        let d = format!("{:02x}", ('B' as u8 ^ rng.gen::<u8>()));
        let e = format!("{:02x}", ('{' as u8 ^ rng.gen::<u8>()));

        if a == "41" && b == "8a" && c == "51" && d == "75" && e == "c3" {
            println!("Seed found: {}", seed);
            found = true;
        } else {
            seed -= 1;
        }
    }
    return seed;
}
```

This gives us:  `Seed found: 1618179277`

From there we are back to soulcrabber. That's it.
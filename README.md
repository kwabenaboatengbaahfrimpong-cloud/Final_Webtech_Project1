# EcoCampus

A recycling rewards system I built for my campus. Students can log their recycling, earn points, and redeem rewards.

## What It Does

I created a platform where users register, log what they recycle (plastic, paper, metal, e-waste), and admins approve the submissions. Once approved, users get points based on weight. They can then spend those points on rewards like cafeteria vouchers or campus merch.

I also added a leaderboard to see who's recycling the most each month.

## Tech I Used

- PHP (no frameworks, just vanilla)
- MySQL database
- Bootstrap for styling
- Basic JavaScript for form checks

## Setup

1. Import `database.sql` into MySQL database
2. Edit `public/includes/config.php` with database credentials
3. Put the folder in `htdocs` if using XAMPP
4. Go to `http://localhost/EcoPoints_Full_Project/public/`

## Making an Admin Account

After registering, run this in the database:

```sql
UPDATE users SET role='admin' WHERE email='youremail@example.com';
```

Then log back in to see the admin panel.

## Main Pages

**For Users:**
- Register/Login
- Dashboard (see points balance)
- Submit recycling logs
- Browse rewards
- Redeem rewards
- Leaderboard

**For Admins:**
- Review submissions (approve/reject)
- Manage materials and bins
- Add/edit rewards
- See all redemptions

## How It Works

1. User submits a recycling log (material type, bin location, quantity)
2. Admin reviews it and can see all the details
3. If approved, points = quantity × points_per_unit (I set this for each material)
4. Points get added to user's balance
5. User can browse rewards and redeem if they have enough points
6. Stock decreases when someone redeems

## Database Tables

I created 7 tables:
- users (accounts and points)
- materials (plastic, paper, etc with point values)
- bins (locations around campus)
- submissions (recycling logs)
- rewards (things users can redeem)
- redemptions (history of what people redeemed)
- login_attempts (for rate limiting)

## Security Features

- Passwords are hashed
- SQL uses prepared statements
- CSRF tokens on forms
- Session-based login
- Admins and users have different access

## Notes

I built this for my web tech course. The idea is to encourage recycling by making it rewarding and competitive with the leaderboard.

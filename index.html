public class User
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Email { get; set; }
    public string PhoneNumber { get; set; }
    public string Password { get; set; }
    public UserRole Role { get; set; }
}

public class Property
{
    public int Id { get; set; }
    public string Place { get; set; }
    public int Area { get; set; }
    public int NumberOfBedrooms { get; set; }
    public int NumberOfBathrooms { get; set; }
    public string NearbyHospitals { get; set; }
    public string NearbyColleges { get; set; }
    public int SellerId { get; set; }
    public User Seller { get; set; }
}

public enum UserRole
{
    Seller,
    Buyer
}
public class AppDbContext : DbContext
{
    public DbSet<User> Users { get; set; }
    public DbSet<Property> Properties { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        optionsBuilder.UseSqlServer("YourConnectionStringHere");
    }
}
public class AccountController : Controller
{
    private readonly AppDbContext _context;

    public AccountController(AppDbContext context)
    {
        _context = context;
    }

    public IActionResult Register() => View();

    [HttpPost]
    public async Task<IActionResult> Register(User user)
    {
        if (ModelState.IsValid)
        {
            user.Role = UserRole.Buyer; // Or Seller based on selection
            _context.Users.Add(user);
            await _context.SaveChangesAsync();
            return RedirectToAction("Login");
        }
        return View(user);
    }

    public IActionResult Login() => View();

    [HttpPost]
    public async Task<IActionResult> Login(string email, string password)
    {
        var user = await _context.Users.SingleOrDefaultAsync(u => u.Email == email && u.Password == password);
        if (user != null)
        {
            // Set session and redirect based on role
            HttpContext.Session.SetInt32("UserId", user.Id);
            return RedirectToAction(user.Role == UserRole.Seller ? "SellerDashboard" : "BuyerDashboard");
        }
        ModelState.AddModelError("", "Invalid login attempt");
        return View();
    }
}
public class SellerController : Controller
{
    private readonly AppDbContext _context;

    public SellerController(AppDbContext context)
    {
        _context = context;
    }

    public IActionResult Dashboard() => View();

    public IActionResult AddProperty() => View();

    [HttpPost]
    public async Task<IActionResult> AddProperty(Property property)
    {
        var sellerId = HttpContext.Session.GetInt32("UserId");
        property.SellerId = sellerId.Value;
        _context.Properties.Add(property);
        await _context.SaveChangesAsync();
        return RedirectToAction("Dashboard");
    }

    public async Task<IActionResult> EditProperty(int id)
    {
        var property = await _context.Properties.FindAsync(id);
        return View(property);
    }

    [HttpPost]
    public async Task<IActionResult> EditProperty(Property property)
    {
        if (ModelState.IsValid)
        {
            _context.Update(property);
            await _context.SaveChangesAsync();
            return RedirectToAction("Dashboard");
        }
        return View(property);
    }

    public async Task<IActionResult> DeleteProperty(int id)
    {
        var property = await _context.Properties.FindAsync(id);
        _context.Properties.Remove(property);
        await _context.SaveChangesAsync();
        return RedirectToAction("Dashboard");
    }
}
public class BuyerController : Controller
{
    private readonly AppDbContext _context;

    public BuyerController(AppDbContext context)
    {
        _context = context;
    }

    public async Task<IActionResult> Index()
    {
        var properties = await _context.Properties.ToListAsync();
        return View(properties);
    }

    public async Task<IActionResult> ViewProperty(int id)
    {
        var property = await _context.Properties.FindAsync(id);
        return View(property);
    }

    public async Task<IActionResult> ExpressInterest(int id)
    {
        var property = await _context.Properties.FindAsync(id);
        // Send notification or email to the seller
        return RedirectToAction("Index");
    }
}
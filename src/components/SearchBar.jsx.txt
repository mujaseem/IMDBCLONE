import { useState } from "react";

const SearchBar = ({ onSearch }) => {
  const [query, setQuery] = useState("");

  const handleSearch = (e) => {
    const value = e.target.value;
    setQuery(value);
    if (value.length > 2) {
      fetch(`https://www.omdbapi.com/?apikey=8d9d8cfe&s=${value}`)
        .then((res) => res.json())
        .then((data) => onSearch(data.Search || []))
        .catch((error) => console.error("Error fetching search results:", error));
    }
  };

  return (
    <input
      type="text"
      placeholder="Search movies..."
      value={query}
      onChange={handleSearch}
      className="search-bar"
    />
  );
};

export default SearchBar;

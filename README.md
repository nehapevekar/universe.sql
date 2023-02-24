# universe.sql
celestial bodies database
--
-- PostgreSQL database dump
--

-- Dumped from database version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)
-- Dumped by pg_dump version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    has_life boolean,
    is_spherical boolean NOT NULL,
    description text NOT NULL,
    age_in_millions_of_years integer,
    distance_from_earth integer,
    name character varying(20) NOT NULL,
    galaxy_types character varying(30)
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(20) NOT NULL,
    description text,
    has_life boolean,
    planet_id integer
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    planet_types character varying(30),
    has_life boolean NOT NULL,
    description text,
    name character varying(20),
    weight numeric
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_and_its_moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet_and_its_moon (
    planet_and_its_moon_id integer NOT NULL,
    name character varying(30),
    moon_name character varying(30),
    moon_id integer NOT NULL,
    planet_id integer NOT NULL
);


ALTER TABLE public.planet_and_its_moon OWNER TO freecodecamp;

--
-- Name: planet_and_its_moon_planet_and_its_moon_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_and_its_moon_planet_and_its_moon_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_and_its_moon_planet_and_its_moon_seq OWNER TO freecodecamp;

--
-- Name: planet_and_its_moon_planet_and_its_moon_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_and_its_moon_planet_and_its_moon_seq OWNED BY public.planet_and_its_moon.planet_and_its_moon_id;


--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(20),
    distance_from_earth integer,
    description text,
    is_spherical boolean NOT NULL,
    galaxy_id integer
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: planet_and_its_moon planet_and_its_moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet_and_its_moon ALTER COLUMN planet_and_its_moon_id SET DEFAULT nextval('public.planet_and_its_moon_planet_and_its_moon_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, true, false, 'Galaxy that includes Solar System', 500, 26, 'Milky Way', 'spiral galaxy');
INSERT INTO public.galaxy VALUES (2, false, false, 'The closest and the best studied great cluster of galaxies', 178, 53, 'Virgo A', 'elliptical spiral galaxy');
INSERT INTO public.galaxy VALUES (3, false, false, 'It is a radio galaxy.one of the earliest radio sourcs discovered', 20, 28, 'Cygnus A', 'elliptical galaxy');
INSERT INTO public.galaxy VALUES (4, false, false, 'one of the few visible to the unaided eye', 1000, 3, 'andromeda', 'barred spiral galaxy');
INSERT INTO public.galaxy VALUES (5, false, false, 'shines brightly at infrared wavelength', 11, 12, '
Cigar', 'elongated elliptical');
INSERT INTO public.galaxy VALUES (6, false, false, 'small irregular galaxy with a mass of about a billion solar masses', 14, 25, 'Canis major dwarf', 'roughly elliptical');


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'luna', 'earth natural satellite', false, 1);
INSERT INTO public.moon VALUES (2, 'europa', '6th largest moon in solar system', false, 2);
INSERT INTO public.moon VALUES (3, 'ganymede', ' largest moon in solar system', false, 2);
INSERT INTO public.moon VALUES (4, 'thebe', ' irregular shape and red in color', false, 2);
INSERT INTO public.moon VALUES (5, 'phobos', ' natural satellite of mars larger than deimos', false, 3);
INSERT INTO public.moon VALUES (6, 'deimos', ' natural satellite of mars smaller than phobos', false, 3);
INSERT INTO public.moon VALUES (7, 'titan', 'largest moon of saturn', false, 6);
INSERT INTO public.moon VALUES (8, 'callisto', '2nd largest moon of jupiter', false, 2);
INSERT INTO public.moon VALUES (9, 'lapetus', '3rd largest moon of saturn', false, 6);
INSERT INTO public.moon VALUES (10, 'titania', 'largest moon of uranus', false, 7);
INSERT INTO public.moon VALUES (11, 'oberon', '2nd largest moon of uranus', false, 7);
INSERT INTO public.moon VALUES (12, 'triton', 'largest moon of neptune', false, 8);
INSERT INTO public.moon VALUES (13, 'neso', 'irregular moon of neptune', false, 8);
INSERT INTO public.moon VALUES (14, 'halimede', 'irregular moon of neptune', false, 8);
INSERT INTO public.moon VALUES (15, 'dysnomia', 'very small moon', false, 10);
INSERT INTO public.moon VALUES (16, 'charon', 'largest moon of pluto', false, 9);
INSERT INTO public.moon VALUES (17, 'nix', 'non-spherical moon', false, 9);
INSERT INTO public.moon VALUES (18, 'kerberos', '2nd smallest  moon of pluto', false, 9);
INSERT INTO public.moon VALUES (19, 'styx', ' smallest  moon of pluto', false, 9);
INSERT INTO public.moon VALUES (20, 'hydra', ' 2nd largest moon of pluto', false, 9);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'rocky planet', true, 'densest planet in solar system', 'earth', 5.792);
INSERT INTO public.planet VALUES (2, 'jovian planet', false, 'biggest planet in our solar system', 'jupiter', 1.898);
INSERT INTO public.planet VALUES (3, 'rocky planet', false, 'red planet', 'mars', 6.39);
INSERT INTO public.planet VALUES (4, 'terrestial planet', false, 'earth sister', 'venus', 4.867);
INSERT INTO public.planet VALUES (5, 'terrestial planet', false, 'smallest in our solar system', 'mercury', 3.285);
INSERT INTO public.planet VALUES (6, 'jovian planet', false, 'second largest planet in our solar system', 'saturn', 5.683);
INSERT INTO public.planet VALUES (7, 'ice giant planet', false, 'ice giant', 'uranus', 8.681);
INSERT INTO public.planet VALUES (8, 'ice giant planet', false, 'coldest in solar sytem', 'neptune', 1.024);
INSERT INTO public.planet VALUES (9, 'dwarf planet', false, 'smaller than our moon', 'pluto', 0.013);
INSERT INTO public.planet VALUES (10, 'dwarf planet', false, 'largest dwarf planet in our solar system ', 'eris', 1.66);
INSERT INTO public.planet VALUES (11, 'dwarf planet', false, 'only  dwarf planet located  in our inner  solar system ', 'ceres', 9.38);
INSERT INTO public.planet VALUES (12, '', false, '', 'marduk', 3.45);


--
-- Data for Name: planet_and_its_moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet_and_its_moon VALUES (1, 'earth', 'luna', 1, 1);
INSERT INTO public.planet_and_its_moon VALUES (2, 'jupiter', 'europa', 2, 2);
INSERT INTO public.planet_and_its_moon VALUES (3, 'jupiter', 'ganymede', 3, 2);
INSERT INTO public.planet_and_its_moon VALUES (4, 'jupiter', 'thebe', 4, 2);
INSERT INTO public.planet_and_its_moon VALUES (5, 'mars', 'phobos', 5, 3);
INSERT INTO public.planet_and_its_moon VALUES (6, 'mars', 'deimos', 6, 3);
INSERT INTO public.planet_and_its_moon VALUES (7, 'saturn', 'titan', 7, 6);
INSERT INTO public.planet_and_its_moon VALUES (8, 'jupiter', 'callisto', 8, 2);
INSERT INTO public.planet_and_its_moon VALUES (9, 'saturn', 'lapetus', 9, 6);
INSERT INTO public.planet_and_its_moon VALUES (10, 'uranus', 'titania', 10, 7);
INSERT INTO public.planet_and_its_moon VALUES (11, 'uranus', 'oberon', 11, 7);
INSERT INTO public.planet_and_its_moon VALUES (12, 'neptune', 'triton', 12, 8);
INSERT INTO public.planet_and_its_moon VALUES (13, 'neptune', 'neso', 13, 8);
INSERT INTO public.planet_and_its_moon VALUES (14, 'neptune', 'halimede', 14, 8);
INSERT INTO public.planet_and_its_moon VALUES (15, 'eris', 'dysnomia', 15, 10);
INSERT INTO public.planet_and_its_moon VALUES (16, 'pluto', 'charon', 16, 9);
INSERT INTO public.planet_and_its_moon VALUES (17, 'pluto', 'nix', 17, 9);
INSERT INTO public.planet_and_its_moon VALUES (18, 'pluto', 'kerberos', 18, 9);
INSERT INTO public.planet_and_its_moon VALUES (19, 'pluto', 'styx', 19, 9);
INSERT INTO public.planet_and_its_moon VALUES (20, 'pluto', 'hydra', 20, 9);


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Sun', 148, 'a hot glowing ball of hydrogen and helium', false, 1);
INSERT INTO public.star VALUES (2, 'UY Scuti', 52, 'an extreme red super giant star ', false, 1);
INSERT INTO public.star VALUES (3, 'MU Cephei', 28, 'garnet star', true, 1);
INSERT INTO public.star VALUES (4, 'Porrima', 38, 'binary star system', false, 2);
INSERT INTO public.star VALUES (5, 'Monch', 34, 'dimmer and cooler than the sun', true, 2);
INSERT INTO public.star VALUES (6, 'Deneb', 14, 'a bluish white supergiant brightest star', false, 3);
INSERT INTO public.star VALUES (7, 'Delta cygni', 13, 'a blue giant star', false, 3);
INSERT INTO public.star VALUES (8, 'Mirach', 22, 'a red giant star in the final stage', true, 4);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 1, false);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 1, false);


--
-- Name: planet_and_its_moon_planet_and_its_moon_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_and_its_moon_planet_and_its_moon_seq', 20, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 1, false);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 1, false);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet_and_its_moon planet_and_its_moon_moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet_and_its_moon
    ADD CONSTRAINT planet_and_its_moon_moon_name_key UNIQUE (moon_name);


--
-- Name: planet_and_its_moon planet_and_its_moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet_and_its_moon
    ADD CONSTRAINT planet_and_its_moon_pkey PRIMARY KEY (planet_and_its_moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

